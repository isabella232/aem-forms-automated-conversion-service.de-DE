---
title: Senden der konvertierten adaptiven Formulare mit einem JSON-Schema an die Datenbank
description: Senden Sie die konvertierten adaptiven Formulare mit einem JSON-Schema an die Datenbank, indem Sie ein Formulardatenmodell erstellen und in einem AEM-Arbeitsablauf darauf verweisen.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: c552f4073ac88ca9016a746116a27a5898df7f7d

---


# Integrieren des adaptiven Formulars mithilfe des AEM-Arbeitsablaufs in die Datenbank {#submit-forms-to-database-using-forms-portal}

Mit dem Dienst zur automatischen Formularkonvertierung können Sie ein nicht-interaktives PDF-Formular, ein Acro Form oder ein XFA-basiertes PDF-Formular in ein adaptives Formular konvertieren. Während Sie den Konvertierungsprozess starten, haben Sie die Möglichkeit, ein adaptives Formular mit oder ohne Datenbindung zu generieren.

Wenn Sie ein adaptives Formular ohne Datenbindungen generieren möchten, können Sie nach der Konvertierung das adaptive Formular in ein Formulardatenmodell, ein XML-Schema oder ein JSON-Schema integrieren. Für das Formulardatenmodell müssen Sie die Felder des adaptiven Formulars manuell mit dem Formulardatenmodell verknüpfen. Wenn Sie jedoch ein adaptives Formular mit Datenbindungen generieren, ordnet der Konvertierungsdienst die adaptiven Formulare automatisch einem JSON-Schema zu und erstellt eine Datenbindung zwischen den im adaptiven Formular und im JSON-Schema verfügbaren Feldern. Anschließend können Sie das adaptive Formular in eine Datenbank Ihrer Wahl integrieren, Daten in das Formular eintragen und dieses über das Formularportal an die Datenbank senden. Ebenso können Sie nach erfolgreicher Integration in die Datenbank Felder im konvertierten adaptiven Formular konfigurieren, um Werte aus der Datenbank abzurufen und Felder des adaptiven Formulars vorab auszufüllen.

Die folgende Abbildung zeigt verschiedene Phasen der Integration eines konvertierten adaptiven Formulars in eine Datenbank:

![Datenbankintegration](assets/integrate-adaptive-form-with-database.png)

Dieser Artikel gibt Anweisungen zu den einzelnen Schritten für die erfolgreiche Ausführung all dieser Integrationsstufen.

## Voraussetzungen {#pre-requisites}

* Einrichten einer AEM 6.4- oder 6.5-Autoreninstanz
* Installieren Sie das [neueste Service Pack](https://helpx.adobe.com/experience-manager/aem-releases-updates.html) für Ihre AEM-Instanz
* Neueste Version des AEM Forms-Add-On-Pakets
* Configure [Automated Forms Conversion service](configure-service.md)
* Einrichten einer Datenbank. Die in der Beispielimplementierung verwendete Datenbank ist MySQL 5.6.24. Sie können das konvertierte adaptive Formular jedoch in jede beliebige Datenbank Ihrer Wahl integrieren.

## Beispiel für ein adaptives Formular {#sample-adaptive-form}

Laden Sie die folgende PDF-Beispieldatei herunter, um den Anwendungsfall zum Integrieren konvertierter adaptiver Formulare in die Datenbank mithilfe eines AEM-Arbeitsablaufs auszuführen.

Sie können das Beispiel-Kontaktformular herunterladen mit:

[Datei laden](assets/sample_contact_us_form.pdf)

Die PDF-Datei dient als Eingabe für den Dienst zur automatischen Formularkonvertierung. Der Dienst konvertiert diese Datei in ein adaptives Formular. Das folgende Bild zeigt das Beispiel eines Kontaktformulars im PDF-Format.

![Beispielformular für einen Kreditantrag](assets/sample_contact_us_form.png)

## Installieren der Datei mysql-connector-java-5.1.39-bin.jar{#install-mysql-connector-java-file}

Führen Sie die folgenden Schritte auf allen Autoren- und Veröffentlichungsinstanzen aus, um die Datei mysql-connector-java-5.1.39-bin.jar zu installieren:

1. Navigieren Sie zu `http://server:port/system/console/depfinder` und suchen Sie nach dem com.mysql.jdbc-Paket.
1. Überprüfen Sie in der Spalte „Exportiert von“, ob das Paket von einem Paket exportiert wird. Fahren Sie fort, wenn das Paket nicht von einem Paket exportiert wird.
1. Navigieren Sie zu `http://server:port/system/console/bundles` und klicken Sie auf **[!UICONTROL Install/Update]**.
1. Click **[!UICONTROL Choose File]** and browse to select the mysql-connector-java-5.1.39-bin.jar file. Aktivieren **[!UICONTROL Start Bundle]** und **[!UICONTROL Refresh Packages]** aktivieren Sie außerdem die Kontrollkästchen.
1. Klicken Sie auf **[!UICONTROL Install]** oder **[!UICONTROL Update]**. Wenn dies abgeschlossen ist, starten Sie den Server neu.
1. (Nur Windows) Deaktivieren Sie die System-Firewall für Ihr Betriebssystem.

## Vorbereiten der Daten für das Formularmodell {#prepare-data-for-form-model}

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herzustellen. Nach dem Generieren eines adaptiven Formulars mithilfe des Konvertierungsprozesses können Sie das Formularmodell basierend auf einem Formulardatenmodell, XSD oder einem JSON-Schema definieren. Sie können eine Datenbank, Microsoft Dynamics oder einen anderen Dienst eines Drittanbieters verwenden, um ein Formulardatenmodell zu erstellen.

In diesem Lernprogramm wird die MySQL-Datenbank als Quelle zum Erstellen eines Formulardatenmodells verwendet. Erstellen Sie ein Schema in der Datenbank und fügen Sie dem Schema eine **contactus**-Tabelle hinzu, basierend auf den Feldern, die im adaptiven Formular verfügbar sind.

![Beispieldaten mysql](assets/db_entries_sample_form.png)

Mit der folgenden DDL-Anweisung können Sie die Tabelle **contactus** in der Datenbank erstellen.

```sql
CREATE TABLE `contactus` (
   `name` varchar(45) NOT NULL,
   `email` varchar(45) NOT NULL,
   `phonenumber` varchar(10) DEFAULT NULL,
   `issuedesc` varchar(1000) DEFAULT NULL,
   PRIMARY KEY (`email`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## Konfigurieren der Verbindung zwischen der AEM-Instanz und der Datenbank {#configure-connection-between-aem-instance-and-database}

Führen Sie die folgenden Konfigurationsschritte aus, um eine Verbindung zwischen der AEM-Instanz und der MYSQL-Datenbank herzustellen:

1. Navigieren Sie zur AEM Web Console-Konfigurationsseite unter `http://server:port/system/console/configMgr`.
1. Find and click to open **[!UICONTROL Apache Sling Connection Pooled DataSource]** in edit mode in the Web Console Configuration. Geben Sie die Werte für die Eigenschaften an, wie in der folgenden Tabelle beschrieben:

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
    <td><p>jdbc:mysql://[host]:[port]/[schema_name]</p></td>
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

Führen Sie nach dem Konfigurieren von MYSQL als Datenquelle die folgenden Schritte aus, um ein Formulardatenmodell zu erstellen:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**.

1. Tippen Sie auf **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.

1. In the **[!UICONTROL Create Form Data Model]** wizard, specify **workflow_submit** as the name for the form data model. Tippen Sie auf **[!UICONTROL Next]**.

1. Select the MYSQL data source that you have configured in the previous section and tap **[!UICONTROL Create]**.

1. Tap **[!UICONTROL Edit]** and expand the data source listed in the left pane to select **contactus** table, **[!UICONTROL get]**, and **[!UICONTROL insert]** services, and tap **[!UICONTROL Add Selected]**.

   ![Beispieldaten mysql](assets/fdm_details_workfdlow_submit.png)

1. Select the data model object in the right pane and tap **[!UICONTROL Edit Properties]**. Wählen Sie **[!UICONTROL get]** und **[!UICONTROL insert]** aus **[!UICONTROL Read Service]** und **[!UICONTROL Write Service]** Dropdown-Listen. Specify the arguments for the Read service and tap **[!UICONTROL Done]**.

1. Wählen Sie auf der **[!UICONTROL Services]** Registerkarte den **[!UICONTROL get]** Dienst aus und tippen Sie auf **[!UICONTROL Edit Properties]**. Wählen Sie die Option **[!UICONTROL Output Model Object]**, deaktivieren Sie den **[!UICONTROL Return array]** Umschalter und tippen Sie auf **[!UICONTROL Done]**.

1. Select the **[!UICONTROL Insert]** service and tap **[!UICONTROL Edit Properties]**. Select the **[!UICONTROL Input Model Object]** and tap **[!UICONTROL Done]**.

1. Tap **[!UICONTROL Save]** to save the form data model.

Sie können das Beispiel-Formulardatenmodell wie folgt herunterladen:

[Datei laden](assets/DownloadedFormsPackage_1497728018502500.zip)

## Generieren adaptiver Formulare mit JSON-Bindung {#generate-adaptive-forms-with-json-binding}

Verwenden Sie den [Dienst für die automatische Formularkonvertierung](convert-existing-forms-to-adaptive-forms.md) zum Konvertieren des [Kontaktformulars](#sample-adaptive-form) in ein adaptives Formular mit Datenbindung. Stellen Sie sicher, dass Sie das **[!UICONTROL Generate adaptive form(s) without data bindings]** Kontrollkästchen beim Generieren des adaptiven Formulars nicht aktivieren.

![Adaptives Formular mit JSON-Bindung](assets/generate_af_with_data_bindings.png)

Select the converted **Contact Us form** available in the **[!UICONTROL output]** folder in **[!UICONTROL Forms & Documents]** and tap **[!UICONTROL Edit]**. Tap **[!UICONTROL Preview]**, enter values in the adaptive form fields and tap **[!UICONTROL Submit]**.

Melden Sie sich bei **crx-repository** an und navigieren Sie zu */content/forms/fp/admin/submit/data*, um die übermittelten Werte im JSON-Format anzuzeigen. Im Folgenden werden die Beispieldaten im JSON-Format gezeigt, wenn Sie das konvertierte adaptive **Kontaktformular** senden:

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

Sie müssen jetzt ein Arbeitsablaufmodell erstellen, das diese Daten verarbeiten und über das in den vorherigen Abschnitten erstellte Formulardatenmodell an die MYSQL-Datenbank senden kann.

## Erstellen Sie ein Arbeitsablaufmodell zur Verarbeitung von JSON-Daten{#create-workflow-model}

Führen Sie die folgenden Schritte aus, um ein Arbeitsablaufmodell zum Senden der adaptiven Formulardaten an die Datenbank zu erstellen:

1. Öffnen Sie die Konsole für Arbeitsablaufmodelle. Die Standardeinstellung ist `https://server:port/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.

1. Wählen Sie **[!UICONTROL Create]** dann **[!UICONTROL Create Model]**. The **[!UICONTROL Add Workflow Model]** dialog appears.

1. Geben Sie den **[!UICONTROL Title]** und **[!UICONTROL Name]** (optional) ein. Zum Beispiel **workflow_json_submit**. Tap **[!UICONTROL Done]** to create the model.

1. Select the workflow model and tap **[!UICONTROL Edit]** to open the model in edit mode. Tippen Sie auf + und fügen Sie **[!UICONTROL Invoke Form Data Model Service]** Schritt zum Workflow-Modell hinzu.

1. Tippen Sie auf den **[!UICONTROL Invoke Form Data Model Service]** Schritt und dann auf ![Konfigurieren](assets/configure_icon.png).

1. Wählen Sie auf der **[!UICONTROL Form Data Model]** Registerkarte das Formulardatenmodell aus, das Sie im **[!UICONTROL Form Data Model path]** Feld erstellt haben, und wählen Sie **[!UICONTROL insert]** aus der **[!UICONTROL Service]** Dropdown-Liste aus.

1. Wählen Sie auf der **[!UICONTROL Input for Service]** Registerkarte **[!UICONTROL Provide input data using literal, variable, or a workflow metadata, and a JSON file]** aus der Dropdown-Liste, aktivieren Sie das **[!UICONTROL Map input fields from input JSON]** Kontrollkästchen, wählen Sie **[!UICONTROL Relative to payload]** und geben Sie als Wert **data.xml** für das **[!UICONTROL Select input JSON document using]** Feld ein.

1. In the **[!UICONTROL Service Arguments]** section, provide the following values for the form data model arguments:

   ![Formulardatenmodelldienst aufrufen](assets/invoke_form_data_model_service.png)

   Beachten Sie, dass die Formulardatenmodellfelder, z. B. contactus Punkt Name dem **afData.afBoundData.data.name1** zugeordnet werden, das auf die JSON-Schemabindungen für das gesendete adaptive Formular verweist.

## Konfigurieren der Übermittlung des adaptiven Formulars {#configure-adaptive-form-submission}

Führen Sie die folgenden Schritte aus, um das adaptive Formular an das Arbeitsablaufmodell zu senden, das Sie im vorherigen Abschnitt erstellt haben:

1. Select the converted Contact Us form available in the **[!UICONTROL output]** folder in **[!UICONTROL Forms & Documents]** and tap **[!UICONTROL Edit]**.

1. Open adaptive form properties by tapping **[!UICONTROL Form Container]** and then tapping ![Configure](assets/configure_icon.png).

1. Wählen Sie im **[!UICONTROL Submission]** Abschnitt **[!UICONTROL Invoke an AEM workflow]** aus der **[!UICONTROL Submit Action]** Dropdown-Liste das Workflow-Modell aus, das Sie im vorherigen Abschnitt erstellt haben, und geben Sie **data.xml** im **[!UICONTROL Data File Path]** -Feld an.

1. Tippen Sie auf ![Speichern](assets/save_icon.png), um die Eigenschaften zu speichern.

1. Tap **[!UICONTROL Preview]**, enter values in the adaptive form fields and tap **[!UICONTROL Submit]**. Die übermittelten Werte werden jetzt in der MYSQL-Datenbanktabelle anstelle von **crx-repository** angezeigt.

## Konfigurieren des adaptiven Formulars, um Werte aus der Datenbank vorab auszufüllen

Führen Sie die folgenden Schritte aus, um das adaptive Formular so zu konfigurieren, dass Werte aus der MYSQL-Datenbank basierend auf dem in der Tabelle definierten Primärschlüssel (in diesem Fall E-Mail) vorab ausgefüllt werden:

1. Tippen Sie im adaptiven Formular auf das Feld **E-Mail** und anschließend auf ![Regel bearbeiten](assets/edit-rules.png).

1. Tippen Sie auf **[!UICONTROL Create]** und wählen Sie **[!UICONTROL is changed]** aus der **[!UICONTROL Select State]** Dropdown-Liste im **[!UICONTROL When]** Abschnitt aus.

1. In the **[!UICONTROL Then]** section, select **[!UICONTROL Invoke Service]** and **get** as the service for the form data model that you have created in a previous section of this article.

1. Select **E-mail** in the **[!UICONTROL Input]** section and the rest three fields of the form data model, **Name**, **Phone Number**, and **Issue Description** in the **[!UICONTROL Output]** section. Tap **[!UICONTROL Done]** to save the settings.

   ![Einstellungen zum Vorab-Ausfüllen der E-Mail konfigurieren](assets/email_prefill_settings.png)

   As a result, based on existing E-mail entries in the MYSQL database, you can prefill the values for the rest three fields in the **[!UICONTROL Preview]** mode of the adaptive form. Wenn Sie beispielsweise aya.tan@xyz.com im Feld **E-Mail** angeben (basierend auf den vorhandenen Daten gemäß Abschnitt [Formulardatenmodell vorbereiten](#prepare-data-for-form-model) dieses Artikels) und das Feld mit der Tabulatortaste verlassen, werden die restlichen drei Felder, **Name**, **Telefonnummer** und **Problembeschreibung** automatisch im adaptiven Formular angezeigt.

Sie können das konvertierte adaptive Formular herunterladen mit:

[Datei laden](assets/DownloadedFormsPackage_1498226829041200.zip)
