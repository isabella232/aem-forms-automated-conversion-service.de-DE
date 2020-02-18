---
title: Senden der konvertierten adaptiven Formulare mit einem JSON-Schema an die Datenbank
description: Senden Sie die konvertierten adaptiven Formulare mit einem JSON-Schema an die Datenbank, indem Sie ein Formulardatenmodell erstellen und in einem AEM-Workflow darauf verweisen.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: b879a0ddecd5370c754dfe9e1bf33121dd5ecc97

---


# Adaptives Formular mit Datenbank mit AEM-Workflow integrieren {#submit-forms-to-database-using-forms-portal}

Der Dienst &quot;Automatisierte Formularkonvertierung&quot;ermöglicht die Konvertierung eines nicht interaktiven PDF-Formulars, eines Acro-Formulars oder eines XFA-basierten PDF-Formulars in ein adaptives Formular. Beim Starten des Konvertierungsprozesses haben Sie die Möglichkeit, ein adaptives Formular entweder mit oder ohne Datenbindungen zu erstellen.

Wenn Sie ein adaptives Formular ohne Datenbindungen erstellen möchten, können Sie das konvertierte adaptive Formular nach der Konvertierung in ein Formulardatenmodell, ein XML-Schema oder ein JSON-Schema integrieren. Für Formulardatenmodell müssen Sie adaptive Formularfelder manuell mit dem Formulardatenmodell verknüpfen. Wenn Sie jedoch ein adaptives Formular mit Datenbindungen generieren, verknüpft der Konvertierungsdienst automatisch die adaptiven Formulare mit einem JSON-Schema und erstellt eine Datenbindung zwischen den im adaptiven Formular verfügbaren Feldern und dem JSON-Schema. Anschließend können Sie das adaptive Formular in eine Datenbank Ihrer Wahl integrieren, Daten im Formular ausfüllen und an die Datenbank senden. Ebenso können Sie nach erfolgreicher Integration in die Datenbank Felder im konvertierten adaptiven Formular konfigurieren, um Werte aus der Datenbank abzurufen und vorab adaptive Formularfelder auszufüllen.

Die folgende Abbildung zeigt die verschiedenen Phasen der Integration eines konvertierten adaptiven Formulars mit einer Datenbank:

![Datenbankintegration](assets/integrate-adaptive-form-with-database.png)

In diesem Artikel werden die schrittweisen Anweisungen zum erfolgreichen Ausführen aller dieser Integrationsschritte beschrieben.

## Voraussetzungen {#pre-requisites}

* AEM 6.5 Autoreninstanz mit dem neuesten AEM 6.5 Service Pack
* Neueste Version des Add-On-Pakets für AEM Forms
* [Automatisierter Forms-Konvertierungsdienst](configure-service.md)
* Eine Datenbank, in die integriert werden soll. Die bei der Beispielimplementierung verwendete Datenbank ist MySQL 5.6.24. Sie können das konvertierte adaptive Formular jedoch in eine beliebige Datenbank Ihrer Wahl integrieren.

## Beispiel für ein adaptives Formular {#sample-adaptive-form}

Um die Verwendungsszenario zur Integration konvertierter adaptiver Formulare in eine Datenbank mithilfe eines AEM-Workflows auszuführen, laden Sie die folgende PDF-Musterdatei herunter.

Sie können das Muster-Kontaktformular herunterladen unter:

[Datei laden](assets/sample_contact_us_form.pdf)

Die PDF-Datei dient als Eingabe für den Dienst &quot;Automatisierte Formularkonvertierung&quot;. Der Dienst konvertiert diese Datei in ein adaptives Formular. Die folgende Abbildung zeigt das Beispiel für das Kontaktformular im PDF-Format.

![Beispielformular für einen Kreditantrag](assets/sample_contact_us_form.png)

## Istallieren Sie mysql-connector-java-5.1.39-bin.jar file {#install-mysql-connector-java-file}

Führen Sie die folgenden Schritte auf allen Autor- und Veröffentlichungsinstanzen aus, um die Datei mysql-connector-java-5.1.39-bin.jar zu installieren:

1. Navigieren Sie zum Paket com.mysql.jdbc `http://server:port/system/console/depfinder` und suchen Sie es.
1. Überprüfen Sie in der Spalte „Exportiert von“, ob das Paket von einem Paket exportiert wird. Fahren Sie fort, wenn das Paket nicht von einem Paket exportiert wird.
1. Navigieren Sie zu `http://server:port/system/console/bundles` und klicken Sie auf **[!UICONTROL Install/Update]**.
1. Click **[!UICONTROL Choose File]** and browse to select the mysql-connector-java-5.1.39-bin.jar file. Wählen Sie außerdem **[!UICONTROL Start Bundle]** und **[!UICONTROL Refresh Packages]** Kontrollkästchen aus.
1. Klicken Sie auf **[!UICONTROL Install]** oder **[!UICONTROL Update]**. Wenn Sie bereit sind, starten Sie den Server neu.
1. (Nur Windows) Schalten Sie die System-Firewall für Ihr Betriebssystem aus.

## Daten für Formularmodell vorbereiten {#prepare-data-for-form-model}

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herzustellen. Nachdem Sie ein adaptives Formular mithilfe des Konvertierungsprozesses erstellt haben, können Sie das Formularmodell auf der Grundlage eines Formulardatenmodells, einer XSD- oder eines JSON-Schemas definieren. Sie können eine Datenbank, Microsoft Dynamics oder einen anderen Drittanbieterdienst verwenden, um ein Formulardatenmodell zu erstellen.

In diesem Lernprogramm wird die MySQL-Datenbank als Quelle zum Erstellen eines Formulardatenmodells verwendet. Erstellen Sie ein Schema in der Datenbank und fügen Sie basierend auf den im adaptiven Formular verfügbaren Feldern die Tabelle **contactus** zum Schema hinzu.

![Musterdaten mysql](assets/db_entries_sample_form.png)

Sie können die folgende DDL-Anweisung verwenden, um die **Kontakttabelle** in der Datenbank zu erstellen.

```sql
CREATE TABLE `contactus` (
   `name` varchar(45) NOT NULL,
   `email` varchar(45) NOT NULL,
   `phonenumber` varchar(10) DEFAULT NULL,
   `issuedesc` varchar(1000) DEFAULT NULL,
   PRIMARY KEY (`email`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## Verbindung zwischen AEM-Instanz und Datenbank konfigurieren {#configure-connection-between-aem-instance-and-database}

Führen Sie die folgenden Konfigurationsschritte aus, um eine Verbindung zwischen der AEM-Instanz und der MYSQL-Datenbank zu erstellen:

1. Go to AEM Web Console Configuration page at `http://server:port/system/console/configMgr`.
1. Klicken Sie auf und suchen Sie **[!UICONTROL Apache Sling Connection Pooled DataSource]** im Bearbeitungsmodus in der Web-Konsolenkonfiguration. Geben Sie die Werte für die Eigenschaften an, wie in der folgenden Tabelle beschrieben:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Eigenschaft</strong></th> 
    <th><strong>Wert</strong></th> 
    </tr> 
    <tr> 
    <td><p>Datenquellenname</p></td> 
    <td><p>Ein Datenquellenname für das Filtern der Treiber aus dem Datenquellenpool.</p></td>
    </tr>
    <tr> 
    <td><p>JDBC-Treiberklasse</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>JDBC-Verbindungs-URI</p></td> 
    <td><p>jdbc:mysql://[Host]:[Anschluss]/[Schemaname]</p></td>
    </tr>
    <tr> 
    <td><p>Benutzername</p></td> 
    <td><p>Ein Benutzername zur Authentifizierung und zum Durchführen von Aktionen auf Datenbanktabellen</p></td>
    </tr>
    <tr> 
    <td><p>Kennwort</p></td> 
    <td><p>Kennwort für den Benutzernamen</p></td>
    </tr>
    <tr> 
    <td><p>Transaktions-Isolierung</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>Max. aktive Verbindungen</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>Max. inaktive Verbindungen</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>Min. inaktive Verbindungen</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Anfangsgröße</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Max. Wartezeit</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>Test zu Leihung</p></td> 
    <td><p>Aktiviert</p></td>
    </tr>
     <tr> 
    <td><p>Test bei inaktiv</p></td> 
    <td><p>Aktiviert</p></td>
    </tr>
     <tr> 
    <td><p>Validierungsanfrage</p></td> 
    <td><p>Beispielwerte sind SELECT 1 (mysql), select 1 von Dual (oracle), SELECT 1 (MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>Timeout für Validierungsanfrage</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

## Formulardatenmodell erstellen {#create-form-data-model}

Nachdem Sie MYSQL als Datenquelle konfiguriert haben, führen Sie die folgenden Schritte aus, um ein Formulardatenmodell zu erstellen:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**.

1. Tippen Sie auf **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.

1. Geben Sie im **[!UICONTROL Create Form Data Model]** Assistenten **workflow_submit** als Namen für das Formulardatenmodell an. Tippen Sie auf **[!UICONTROL Next]**.

1. Wählen Sie die MYSQL-Datenquelle, die Sie im vorherigen Abschnitt konfiguriert haben, und tippen Sie auf **[!UICONTROL Create]**.

1. Tippen Sie auf **[!UICONTROL Edit]** und erweitern Sie die im linken Bereich aufgelistete Datenquelle, um die Tabelle **contactus** , **[!UICONTROL get]** und **[!UICONTROL insert]** services auszuwählen, und tippen Sie auf **[!UICONTROL Add Selected]**.

   ![Musterdaten mysql](assets/fdm_details_workfdlow_submit.png)

1. Wählen Sie im rechten Bereich das Datenmodellobjekt aus und tippen Sie auf **[!UICONTROL Edit Properties]**. Wählen Sie **[!UICONTROL get]** und **[!UICONTROL insert]** aus **[!UICONTROL Read Service]** und **[!UICONTROL Write Service]** Dropdownlisten. Geben Sie die Argumente für den Read-Dienst an und tippen Sie auf **[!UICONTROL Done]**.

1. Wählen Sie auf der **[!UICONTROL Services]** Registerkarte den **[!UICONTROL get]** Dienst aus und tippen Sie auf **[!UICONTROL Edit Properties]**. Wählen Sie die Option **[!UICONTROL Output Model Object]**, deaktivieren Sie den **[!UICONTROL Return array]** Umschalter und tippen Sie auf **[!UICONTROL Done]**.

1. Select the **[!UICONTROL Insert]** service and tap **[!UICONTROL Edit Properties]**. Select the **[!UICONTROL Input Model Object]** and tap **[!UICONTROL Done]**.

1. Tap **[!UICONTROL Save]** to save the form data model.

Sie können das Musterdatenmodell des Formulars wie folgt herunterladen:

[Datei laden](assets/DownloadedFormsPackage_1497728018502500.zip)

## Erstellen adaptiver Formulare mit JSON-Bindung {#generate-adaptive-forms-with-json-binding}

Verwenden Sie den [automatisierten Forms-Konvertierungsdienst, um das ](convert-existing-forms-to-adaptive-forms.md)Kontaktformular[ in ein adaptives Formular mit Datenbindung zu konvertieren](#sample-adaptive-form) . Stellen Sie sicher, dass Sie das **[!UICONTROL Generate adaptive form(s) without data bindings]** Kontrollkästchen beim Generieren des adaptiven Formulars nicht aktivieren.

![Adaptives Formular mit JSON-Bindung](assets/generate_af_with_data_bindings.png)

Wählen Sie das konvertierte **Kontaktformular** aus, das im **[!UICONTROL output]** Ordner in verfügbar ist, **[!UICONTROL Forms & Documents]** und tippen Sie auf **[!UICONTROL Edit]**. Tippen Sie auf **[!UICONTROL Preview]**, geben Sie Werte in die Felder des adaptiven Formulars ein und tippen Sie auf **[!UICONTROL Submit]**.

Melden Sie sich bei **crx-repository** an und navigieren Sie zu */content/forms/fp/admin/submit/data* , um die gesendeten Werte im JSON-Format anzuzeigen. Im Folgenden finden Sie die Beispieldaten im JSON-Format, wenn Sie das konvertierte adaptive **Kontaktformular** senden:

```json
{
  "afData": {
    "afUnboundData": {
      "data": {}
    },
    "afBoundData": {
      "data": {
        "name1": "Gloria",
        "email": "abc@xyz.com",
        "phone_number": "2346578965",
        "issue_description": "Test message"
      }
    },
    "afSubmissionInfo": {
      "computedMetaInfo": {},
      "stateOverrides": {},
      "signers": {},
      "afPath": "/content/dam/formsanddocuments/docs_conversion/output/sample_form_json",
      "afSubmissionTime": "20191204014007"
    }
  }
}
```

Sie müssen jetzt ein Workflow-Modell erstellen, das diese Daten verarbeiten und mit dem in den vorherigen Abschnitten erstellten Formulardatenmodell an die MYSQL-Datenbank senden kann.

## Workflow-Modell zur Verarbeitung von JSON-Daten erstellen {#create-workflow-model}

Führen Sie die folgenden Schritte aus, um ein Workflow-Modell zum Senden der Daten des adaptiven Formulars an die Datenbank zu erstellen:

1. Öffnen Sie die Konsole für Workflow-Modelle. The default URL is `https://server:port/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.

1. Wählen Sie **[!UICONTROL Create]** dann **[!UICONTROL Create Model]**. The **[!UICONTROL Add Workflow Model]** dialog appears.

1. Geben Sie den **[!UICONTROL Title]** und **[!UICONTROL Name]** (optional) ein. Beispiel: **workflow_json_submit**. Tippen Sie auf **[!UICONTROL Done]** , um das Modell zu erstellen.

1. Wählen Sie das Workflow-Modell aus und tippen Sie auf , **[!UICONTROL Edit]** um das Modell im Bearbeitungsmodus zu öffnen. Tippen Sie auf + und fügen Sie **[!UICONTROL Invoke Form Data Model Service]** Schritt zum Workflow-Modell hinzu.

1. Tippen Sie auf den **[!UICONTROL Invoke Form Data Model Service]** Schritt und dann auf ![Konfigurieren](assets/configure_icon.png).

1. Wählen Sie auf der **[!UICONTROL Form Data Model]** Registerkarte das Formulardatenmodell aus, das Sie im **[!UICONTROL Form Data Model path]** Feld erstellt haben, und wählen Sie **[!UICONTROL insert]** aus der **[!UICONTROL Service]** Dropdownliste aus.

1. Wählen Sie auf der **[!UICONTROL Input for Service]** Registerkarte **[!UICONTROL Provide input data using literal, variable, or a workflow metadata, and a JSON file]** aus der Dropdownliste das Kontrollkästchen **[!UICONTROL Map input fields from input JSON]** , wählen Sie **[!UICONTROL Relative to payload]** und geben Sie als Wert für das **Feld &quot;data.xml** **[!UICONTROL Select input JSON document using]**&quot;ein.

1. Geben Sie im **[!UICONTROL Service Arguments]** Abschnitt die folgenden Werte für die Formulardatenmodellargumente ein:

   ![Formulardatenmodelldienst aufrufen](assets/invoke_form_data_model_service.png)

   Beachten Sie, dass die Formulardatenmodellfelder, z. B. contactus dot name, **afData.afBoundData.data.name1** zugeordnet werden, was sich auf die JSON-Schemabindungen für das gesendete adaptive Formular bezieht.

## Übermitteln adaptiver Formulare konfigurieren {#configure-adaptive-form-submission}

Führen Sie die folgenden Schritte aus, um das adaptive Formular an das Workflow-Modell zu senden, das Sie im vorherigen Abschnitt erstellt haben:

1. Wählen Sie das konvertierte Kontaktformular aus, das im **[!UICONTROL output]** Ordner in verfügbar ist, **[!UICONTROL Forms & Documents]** und tippen Sie auf **[!UICONTROL Edit]**.

1. Öffnen Sie die Eigenschaften des adaptiven Formulars, indem Sie auf tippen **[!UICONTROL Form Container]** und dann auf ![Konfigurieren](assets/configure_icon.png)tippen.

1. Wählen Sie im **[!UICONTROL Submission]** Abschnitt **[!UICONTROL Invoke an AEM workflow]** aus der **[!UICONTROL Submit Action]** Dropdownliste das Workflow-Modell aus, das Sie im vorherigen Abschnitt erstellt haben, und geben Sie **data.xml** im **[!UICONTROL Data File Path]** Feld an.

1. Tippen Sie auf ![Speichern](assets/save_icon.png), um die Eigenschaften zu speichern.

1. Tippen Sie auf **[!UICONTROL Preview]**, geben Sie Werte in die Felder des adaptiven Formulars ein und tippen Sie auf **[!UICONTROL Submit]**. Die gesendeten Werte werden jetzt in der MYSQL-Datenbanktabelle anstatt im **CRX-Repository** angezeigt.

## Adaptives Formular zum Vorausfüllen von Werten aus der Datenbank konfigurieren

Führen Sie die folgenden Schritte aus, um das adaptive Formular so zu konfigurieren, dass Werte aus der MYSQL-Datenbank basierend auf dem in der Tabelle definierten Primärschlüssel vorausgefüllt werden (E-Mail in diesem Fall):

1. Tippen Sie im adaptiven Formular auf das Feld **E-Mail** und dann auf Regel ![bearbeiten](assets/edit-rules.png).

1. Tippen Sie auf **[!UICONTROL Create]** und wählen Sie **[!UICONTROL is changed]** aus der **[!UICONTROL Select State]** Dropdownliste im **[!UICONTROL When]** Abschnitt aus.

1. Wählen Sie im **[!UICONTROL Then]** Abschnitt den Dienst für das Formulardatenmodell aus, den Sie in einem vorherigen Abschnitt dieses Artikels erstellt haben, **[!UICONTROL Invoke Service]** und **erhalten** Sie ihn.

1. Wählen Sie **E-Mail** im Abschnitt und die übrigen drei Felder des Formulardatenmodells, **[!UICONTROL Input]** Name **,** Telefonnummer **und** Problembeschreibung **im** **[!UICONTROL Output]** Abschnitt aus. Tap **[!UICONTROL Done]** to save the settings.

   ![E-Mail-Vorgabeeinstellungen konfigurieren](assets/email_prefill_settings.png)

   Daher können Sie die Werte für die übrigen drei Felder im **[!UICONTROL Preview]** Modus des adaptiven Formulars vorab ausfüllen, wenn Sie in der MYSQL-Datenbank vorhandene E-Mail-Einträge verwenden. Wenn Sie z. B. aya.tan@xyz.com im Feld &quot; **E-Mail** &quot;(basierend auf vorhandenen Daten im Abschnitt &quot;Formulardatenmodell[ vorbereiten&quot;) angeben und die Registerkarte außerhalb des Felds verlassen, werden die übrigen drei Felder ](#prepare-data-for-form-model)Name **,** Telefonnummer **und** Problembeschreibung **** automatisch im adaptiven Formular angezeigt.

Sie können das konvertierte Beispiel-adaptive Formular wie folgt herunterladen:

[Datei laden](assets/DownloadedFormsPackage_1498226829041200.zip)
