---
title: Empfohlene datenquellenbasierte Vorlade- und Übermittlungsarbeitsabläufe für adaptive Formulare
seo-title: Optionen zum Vorausfüllen und Senden für adaptive Formulare
description: Auf Datenquellen basierende Vorlade- und Übermittlungsarbeitsabläufe für adaptive Formulare, die mit dem Automatisierten Forms-Konvertierungsdienst generiert wurden.
seo-description: Auf Datenquellen basierende Vorlade- und Übermittlungsarbeitsabläufe für adaptive Formulare, die mit dem Automatisierten Forms-Konvertierungsdienst generiert wurden.
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
translation-type: tm+mt
source-git-commit: f598871fd41c402f98d94d7b2174ab8b2e487075

---


# Empfohlene datenquellenbasierte Vorlade- und Übermittlungsarbeitsabläufe für adaptive Formulare {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

Sie können eine der folgenden Datenquellen für adaptive Formulare verwenden, die mithilfe des Dienstes Automatisierte Formularkonvertierung konvertiert werden:

* Formulardatenmodell, OData oder jeder andere Drittanbieter-Dienst
* JSON-Schema
* XSD-Schema

Je nach Datenquelle können Sie ein adaptives Formular mit oder ohne Datenmodell erstellen.

In diesem Artikel werden die empfohlenen Arbeitsabläufe zum Vorausfüllen von Feldwerten und Übermittlungsoptionen beschrieben, nachdem eine Datenquelle ausgewählt und ein adaptives Formular mit dem Konvertierungsdienst generiert wurde.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Datenquelle</strong></th> 
   <th><strong>Empfohlener Arbeitsablauf</strong></th> 
  </tr> 
  <tr> 
   <td><p>Formulardatenmodell, OData oder jeder andere Drittanbieter-Dienst</p></td> 
   <td> 
    <p><strong>Option 1</strong>: Sie wählen Formulardatenmodell, OData oder einen anderen Drittanbieterdienst als Datenquelle aus. Sie <a href="#generate-adaptive-forms-with-no-data-binding">erstellen ein adaptives Formular ohne Datenbindung</a> mit dem Dienst "Automatisierte Formularkonvertierung". Sie binden die Felder des adaptiven Formulars manuell an die Entitäten des Formulardatenmodells und verwenden die Option "Formulardatenmodell-Vorfülldienst", um Feldwerte im Voraus auszufüllen. Verwenden Sie die Option "Mit Formulardatenmodell senden", um das adaptive Formular zu senden.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>Option 2</strong>: Sie wählen Formulardatenmodell, OData oder einen anderen Drittanbieterdienst als Datenquelle aus. Sie <a href="#generate-adaptive-forms-with-no-data-binding">erstellen ein adaptives Formular ohne Datenbindung</a> mit dem Dienst "Automatisierte Formularkonvertierung". Sie binden die Felder des adaptiven Formulars mit dem Regeleditor, um Feldwerte im Voraus auszufüllen. Ändern Sie bei Bedarf die Feldwerte und senden Sie Daten an das CRX-Repository.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>Eine schrittweise Anleitung zum Ausführen dieser Workflows finden Sie unter Datenbank, OData oder Dienste von Drittanbietern als Datenquelle <a href="#sqldatasource">verwenden.</a></p> </td> 
  </tr>
  <tr>
  <td><p>JSON-Schema </p></td> 
   <td> 
    <p>Sie wählen JSON-Schema als Datenquelle aus. Basierend auf der ausgewählten Datenquelle:</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Option 1</strong>: Sie <a href="#generate-adaptive-forms-with-no-data-binding">generieren ein adaptives Formular ohne Datenbindung</a> mit dem Dienst "Automatisierte Formularkonvertierung"und konfigurieren das JSON-Schema als Datenquelle. Sie binden die Felder des adaptiven Formulars manuell an das JSON-Schema und <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">verwenden eines der unterstützten Protokolle</a> , um Feldwerte im Voraus auszufüllen. Ändern Sie bei Bedarf die Feldwerte und senden Sie Daten an das CRX-Repository.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Eine schrittweise Anleitung zum Ausführen der Workflows finden Sie unter JSON-Schema als Datenquelle <a href="#jsondatasource">verwenden.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Option 2</strong>: Sie <a href="#generate-adaptive-forms-with-json-binding">erstellen ein adaptives Formular mit JSON-Datenbindung</a> mithilfe des Dienstes "Automatisierte Formularkonvertierung". Die Funktion zum Vorausfüllen und zum Senden von Formularen ist nahtlos verfügbar. Sie benötigen keine Konfigurationsschritte.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>Eine schrittweise Anleitung zum Ausführen der Workflows finden Sie unter JSON-Schema als Datenquelle <a href="#jsonwithdatabinding">verwenden.</a></p> </td> 
  </tr>
  <tr>
  <td><p>XSD-Schema</p></td> 
   <td> 
    <p>Sie wählen XSD-Schema als Datenquelle aus. Basierend auf der ausgewählten Datenquelle <a href="#generate-adaptive-forms-with-no-data-binding">erstellen Sie mit dem Dienst für die automatisierte Formularkonvertierung ein adaptives Formular ohne Datenbindung</a> und konfigurieren das XSD-Schema als Datenquelle. Sie binden die Felder des adaptiven Formulars manuell an das XSD-Schema und <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">verwenden eines der unterstützten Protokolle</a> , um Feldwerte im Voraus auszufüllen. Ändern Sie bei Bedarf die Feldwerte und senden Sie Daten an das CRX-Repository.</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Eine schrittweise Anleitung zum Ausführen der Workflows finden Sie unter XSD-Schema als Datenquelle <a href="#xsddatasource">verwenden.</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


Weitere Informationen zum Dienst &quot;Automatisierte Formularkonvertierung&quot;finden Sie in den folgenden Artikeln:

* [Einführung in den Dienst für die automatisierte Formularkonvertierung](introduction.md)
* [Konfigurieren des Dienstes &quot;Automatisierte Formularkonvertierung&quot;](configure-service.md)
* [Druckformulare in adaptive Formulare konvertieren](convert-existing-forms-to-adaptive-forms.md)
* [Überprüfen und Korrigieren konvertierter Formulare](review-correct-ui-edited.md)

Die in diesem Artikel bereitgestellten Informationen basieren auf der Annahme, dass jeder, der ihn liest, grundlegende Kenntnisse der Konzepte adaptiver Formulare besitzt.

## Voraussetzungen {#pre-requisites}

* Configure an [AEM author instance](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* Konfigurieren des Dienstes [&quot;Automatisierte Formularkonvertierung&quot;in der AEM-Autoreninstanz](configure-service.md)

## Beispiel für ein adaptives Formular {#sample-adaptive-form}

Um die Anwendungsfälle zum Vorausfüllen von Feldwerten in einem adaptiven Formular auszuführen und sie an die Datenquelle zu senden, laden Sie die folgende PDF-Musterdatei herunter.

Musterformular für einen Kreditantrag

[Datei laden](assets/sample_loan_application_form.pdf)

Die PDF-Datei dient als Eingabe für den Dienst &quot;Automatisierte Formularkonvertierung&quot;. Der Dienst konvertiert diese Datei in ein adaptives Formular. Die folgende Abbildung zeigt den Beispielkreditantrag im PDF-Format.

![Beispielformular für einen Kreditantrag](assets/sample_form_new.png)

## Daten für Formularmodell vorbereiten {#prepare-data-for-form-model}

Mit der AEM Forms-Datenintegration können Sie unterschiedliche Datenquellen konfigurieren und Verbindungen zu ihnen herzustellen. Nachdem Sie ein adaptives Formular mithilfe des Konvertierungsprozesses erstellt haben, können Sie das Formularmodell auf der Grundlage eines Formulardatenmodells, einer XSD- oder eines JSON-Schemas definieren. Sie können eine Datenbank, Microsoft Dynamics oder einen anderen Drittanbieterdienst verwenden, um ein Formulardatenmodell zu erstellen.

In diesem Lernprogramm wird die MySQL-Datenbank als Quelle zum Erstellen eines Formulardatenmodells verwendet. Erstellen Sie in der Datenbank ein **Kreditanwendungsschema** und fügen Sie basierend auf den im adaptiven Formular verfügbaren Feldern eine **Bewerbertabelle** zum Schema hinzu.

![Musterdaten mysql](assets/sample_data_mysql.png)

Sie können die folgende DDL-Anweisung verwenden, um die **Bewerbertabelle** in der Datenbank zu erstellen.

```sql
CREATE TABLE `applicant` (
   `name` varchar(45) DEFAULT NULL,
   `address` varchar(45) DEFAULT NULL,
   `phonenumber` int(11) NOT NULL,
   `email` varchar(45) DEFAULT NULL,
   `occupation` varchar(45) DEFAULT NULL,
   `annualsalary` varchar(45) DEFAULT NULL,
   `familymembers` int(11) DEFAULT NULL,
   PRIMARY KEY (`phonenumber`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Wenn Sie ein XSD-Schema als Formularmodell verwenden, um die Anwendungsfälle auszuführen, erstellen Sie eine XSD-Datei mit folgendem Text:

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="http://adobe.com/sample.xsd"
                    xmlns="http://adobe.com/sample.xsd"
                    xmlns:xs="http://www.w3.org/2001/XMLSchema">

<xs:element name="sample" type="SampleType"/>

  <xs:complexType name="SampleType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
   <xs:element name="address" type="xs:string"/>
   <xs:element name="phonenumber" type="xs:int"/>
   <xs:element name="email" type="xs:string"/>
   <xs:element name="occupation" type="xs:string"/>
   <xs:element name="annualsalary" type="xs:string"/>
   <xs:element name="familymembers" type="xs:string"/>
 </xs:sequence>
  </xs:complexType>

  </xs:schema>
```

Oder laden Sie das XSD-Schema in das lokale Dateisystem herunter.

Beispiel für eine Kreditanwendung XSD-Schema

[Datei laden](assets/loanapplication.xsd)

Weitere Informationen zur Verwendung des XSD-Schemas als Formularmodell in adaptiven Formularen finden Sie unter [Erstellen adaptiver Formulare mit dem XML-Schema](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html).

Wenn Sie ein JSON-Schema als Formularmodell zum Ausführen der Anwendungsfälle verwenden, erstellen Sie eine JSON-Datei mit folgendem Text:

```JSON
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "definitions": {
        "loanapplication": {
            "type": "object",
            "properties": {
                "name": {
                    "type": "string"
                },
                "address": {
                    "type": "string"
                },
    "phonenumber": {
                    "type": "number"
                },
    "email": {
                    "type": "string"
                },
    "occupation": {
                    "type": "string"
                },
    "annualsalary": {
                    "type": "string"
                },
    "familymembers": {
                    "type": "number"
                }
            }
        }
 },
 "type": "object",
    "properties": {
        "employee": {
            "$ref": "#/definitions/loanapplication"
        }
    }
}
```

Oder laden Sie das JSON-Schema in das lokale Dateisystem herunter.

JSON-Schema für Musterleihanwendung

[Datei laden](assets/demo_schema.json)

Weitere Informationen zur Verwendung des JSON-Schemas als Formularmodell in adaptiven Formularen finden Sie unter [Erstellen adaptiver Formulare mit dem JSON-Schema](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html).

## Erstellen adaptiver Formulare ohne Datenbindung {#generate-adaptive-forms-with-no-data-binding}

Verwenden Sie den [automatisierten Forms-Konvertierungsdienst, um das ](convert-existing-forms-to-adaptive-forms.md)Beispiel-Kreditantragsformular[ in ein adaptives Formular ohne Datenbindung zu konvertieren](#sample-adaptive-form) . Stellen Sie sicher, dass Sie das **[!UICONTROL Generate adaptive form(s) without data bindings]** Kontrollkästchen aktivieren, um das adaptive Formular ohne Datenbindung zu erstellen.

![Adaptives Formular ohne Datenbindung](assets/generate_af_without_binding.png)

Wählen Sie nach dem Generieren eines adaptiven Formulars ohne Datenbindung eine Datenquelle für das adaptive Formular aus:

* [Datenbank, OData oder ein Drittanbieter-Dienst](#sqldatasource)
* [JSON-Schema](#jsondatasource)
* [XSD-Schema](#xsddatasource)

>[!NOTE]
> Wenn das adaptive Formular, das Sie mit dem Automatisierten Forms-Konvertierungsdienst konvertieren, mehrere Felder mit demselben Namen enthält, stellen Sie sicher, dass diese Felder an Datenquellen-Entitäten gebunden sind, um einen möglichen Datenverlust während der Übermittlung zu vermeiden.


### Datenbank, OData oder Dienste von Drittanbietern als Datenquelle verwenden {#sqldatasource}

Verwendungsfall: Sie erstellen ein adaptives Formular ohne Datenbindung mit dem Dienst &quot;Automatisierte Formularkonvertierung&quot;und konfigurieren die MYSQL-Datenbank als Datenquelle. Sie binden die Felder des adaptiven Formulars manuell an Formulardatenmodellentitäten und verwenden die **[!UICONTROL Form Data Model Prefill Service]** Option zum Vorausfüllen von Feldwerten. Sie verwenden die **[!UICONTROL Submit using Form Data Model]** Option zum Senden des adaptiven Formulars.

Vor dem Ausführen des Anwendungsfalls:

* [MySQL-Datenbank als Datenquelle konfigurieren](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [Formulardatenmodell erstellen](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

Erstellen Sie auf der Grundlage des Anwendungsfalls das **Formulardatenmodell für die Anwendung** und binden Sie das Argument für den Lesedienst an einen **[!UICONTROL Literal]** Wert. Der Literalwert für die Telefonnummer muss aus einem der Datensätze bestehen, die im Schema **für Antragsteller** der MySQL-Datenbank konfiguriert sind. Die Dienste verwenden den Wert als Argument, um Details aus der Datenquelle abzurufen. Sie können auch [Benutzerprofilattribut oder Attribut](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument) anfordern in der **[!UICONTROL Binding To]** Dropdownliste auswählen

![Konfigurieren eines Formulardatenmodells](assets/configure_model_object.png)

>[!NOTE]
>
>Stellen Sie sicher, dass Sie dem Formulardatenmodell Dienste **abrufen** und **einfügen** , konfigurieren und testen, bevor Sie den Anwendungsfall ausführen.

Führen Sie die folgenden Schritte aus:

1. Wählen Sie das konvertierte **Beispiel-Kreditantragsformular** aus, das im **[!UICONTROL output]** Ordner verfügbar ist, und tippen Sie auf **[!UICONTROL Properties]**.
1. Tippen Sie auf die **[!UICONTROL Form Model]** Registerkarte, wählen Sie **[!UICONTROL Form Data Model]** aus der **[!UICONTROL Select From]** Dropdown-Liste und tippen Sie auf **[!UICONTROL Select Form Data Model]** , um das **Formulardatenmodell** für die Anwendung auszuwählen. Tap **[!UICONTROL Save & Close]** to save the form.
1. Wählen Sie das **Beispiel-Kreditantragsformular** aus und tippen Sie auf **[!UICONTROL Edit]**.
1. Tippen Sie auf der **[!UICONTROL Content]** Registerkarte auf das Symbol Konfigurieren:

   ![Formularcontainer konfigurieren](assets/configure_form_container.png)

   1. Wählen Sie im **[!UICONTROL Basic]** Abschnitt **[!UICONTROL Form Data Model Prefill service]** aus der **[!UICONTROL Prefill Service]** Dropdownliste aus.

   1. Wählen Sie im **[!UICONTROL Submission]** Abschnitt **[!UICONTROL Submit using Form Data Model]** aus der **[!UICONTROL Submit Action]** Dropdownliste aus.

   1. Wählen Sie das Datenmodell mithilfe des **[!UICONTROL Data Model to submit]** Felds aus.
   1. Tap ![done icon](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) to save the properties.

1. Tippen Sie auf das Textfeld &quot;Name des Antragstellers&quot;und wählen Sie das ![Symbol](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) &quot;Konfigurieren&quot;.

   1. Wählen Sie im Feld &quot;Bindungsreferenz&quot; **Bewerber** > **Name** und tippen Sie auf das ![Fertig-Symbol](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) , um die Eigenschaften zu speichern. Erstellen Sie auf ähnliche Weise eine Datenbindung für **Adresse**, **Telefonnummer**, **E-Mail**, **Beruf**, **Jahresgehalt (in Dollar)****undNein. von Feldern mit abhängigen Familienmitgliedern** mit den Formulardatenmodellentitäten.
   ![Bindungsreferenzen](assets/bind_references.png)

1. Tippen Sie **[!UICONTROL Preview]** auf , um die vorausgefüllten Feldwerte des adaptiven Formulars anzuzeigen.
1. Ändern Sie bei Bedarf die Feldwerte und senden Sie das adaptive Formular. Die Feldwerte werden an die MySQL-Datenbank gesendet. Sie können die **Bewerbertabelle** in der Datenbank aktualisieren, um die aktualisierten Werte in der Tabelle anzuzeigen.

**** Verwendungsfall: Sie erstellen ein adaptives Formular ohne Datenbindung mit dem Dienst &quot;Automatisierte Formularkonvertierung&quot;und konfigurieren die MYSQL-Datenbank als Datenquelle. Sie binden die Felder des adaptiven Formulars mit dem Regeleditor, um Feldwerte im Voraus auszufüllen. Ändern Sie bei Bedarf die Feldwerte und senden Sie Daten an das CRX-Repository.

Führen Sie die folgenden Schritte aus, um mithilfe des [Regeleditors](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html) Formulardatenmodelldienst zum Binden von Feldern und Vorausfüllen von Werten in einem adaptiven Formular aufzurufen:

1. Wählen Sie das **Beispiel-Kreditantragsformular** im **[!UICONTROL output]** Ordner aus und tippen Sie auf **[!UICONTROL Edit]**.
1. Tippen Sie auf der **[!UICONTROL Content]** Registerkarte auf das Symbol Konfigurieren:

   ![Formularcontainer konfigurieren](assets/configure_form_container.png)

   Wählen Sie im **[!UICONTROL Basic]** Abschnitt **[!UICONTROL Form Data Model Prefill service]** aus der **[!UICONTROL Prefill Service]** Dropdownliste aus.

1. Tippen Sie auf das **[!UICONTROL Applicant Name]** Textfeld und dann auf **[!UICONTROL Edit Rules]**.

   ![Regeln bearbeiten, um Datenbindung zu erstellen](assets/edit_rules_bind_reference.png)

1. Tippen Sie auf **[!UICONTROL Create]** der Seite &quot;Regeleditor&quot;.
1. Auf der **[!UICONTROL Rule Editor]** Seite:

   1. Wählen Sie einen Status für das Textfeld &quot;Name des Antragstellers&quot;aus. Dies **[!UICONTROL is initialized]** führt beispielsweise zur Ausführung der **[!UICONTROL Then]** Bedingung, wenn Sie das Formular im **[!UICONTROL Preview]** Modus wiedergeben.

   1. Wählen Sie im **[!UICONTROL Then]** Abschnitt **[!UICONTROL Invoke Service]** aus der **[!UICONTROL Select Action]** Dropdownliste aus. Alle Dienste Ihrer Forms-Instanz werden in der Dropdownliste angezeigt.

   1. Wählen Sie einen **[!UICONTROL Get]** Dienst aus dem Abschnitt mit den Formulardatenmodellen. Das Eingabefeld zeigt die **Telefonnummer** an, die der für das **antragstellende** Datenmodell definierte Primärschlüssel ist. Das System ruft die Werte im adaptiven Formular für Felder im Abschnitt &quot;Ausgabe&quot;ab und füllt sie vorab aus, basierend auf diesem Feld.

   1. Erstellen Sie mithilfe des Abschnitts &quot;Ausgabe&quot;eine Bindung für die Felder des adaptiven Formulars mit den Formulardatenmodellentitäten. Binden Sie beispielsweise das Feld **[!UICONTROL Applicant Name]** für adaptive Formulare an die **Namenentität** .

   1. Tippen Sie auf **[!UICONTROL Done]**. Tippen Sie **[!UICONTROL Done]** erneut auf der Seite &quot;Regeleditor&quot;.
   ![Regeleditor zum Binden von Verweisen](assets/rule_editor_bind_references.png)

1. Tippen Sie **[!UICONTROL Preview]** auf , um die vorausgefüllten Feldwerte des adaptiven Formulars anzuzeigen.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass die **[!UICONTROL Return Array]** Eigenschaft im mit dem adaptiven Formular verknüpften Formulardatenmodell für die Eigenschaft **get** -Dienst auf OFF eingestellt ist.

1. Ändern Sie bei Bedarf die Feldwerte und senden Sie das adaptive Formular. Die gesendeten Daten sind im CRX-Repository unter folgendem Speicherort verfügbar:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### JSON-Schema als Datenquelle verwenden {#jsondatasource}

**** Verwendungsfall: Sie erstellen ein adaptives Formular ohne Datenbindung mit dem Dienst &quot;Automatisierte Formularkonvertierung&quot;und konfigurieren das JSON-Schema als Datenquelle. Sie binden die Felder des adaptiven Formulars manuell an das JSON-Schema und verwenden die Option &quot; **Vorschau mit Daten** &quot;zum Vorausfüllen der Feldwerte. Ändern Sie bei Bedarf die Feldwerte und senden Sie Daten an das CRX-Repository.

Bevor Sie den Anwendungsfall ausführen, stellen Sie sicher, dass Sie über Folgendes verfügen:

* [ein gültiges JSON-Schema, das mit der JSON-Schemastruktur konform ist](#prepare-data-for-form-model)
* [ein adaptives Formular ohne Datenbindung](#generate-adaptive-forms-with-no-data-binding)

Führen Sie die folgenden Schritte aus:

1. Wählen Sie das konvertierte **Beispiel-Kreditantragsformular** aus, das im Ordner &quot; **output** &quot;verfügbar ist, und tippen Sie auf **[!UICONTROL Properties]**.
1. Tippen Sie auf die **[!UICONTROL Form Model]** Registerkarte, wählen Sie **[!UICONTROL Schema]** aus der **[!UICONTROL Select From]** Dropdownliste und tippen Sie auf , **[!UICONTROL Select Schema]** , um das **demo.schema-JSON** -Schema hochzuladen, das im lokalen Dateisystem gespeichert wurde. Tap **[!UICONTROL Save & Close]** to save the form.
1. Wählen Sie das **Beispiel-Kreditantragsformular** aus und tippen Sie auf **[!UICONTROL Edit]**.
1. Tippen Sie auf das Textfeld &quot;Name des Antragstellers&quot;und wählen Sie das ![Symbol](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) &quot;Konfigurieren&quot;.

   Wählen Sie im Feld &quot;Bindungsreferenz&quot; **Bewerber** > **Name** und tippen Sie auf das ![Fertig-Symbol](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) , um die Eigenschaften zu speichern. Erstellen Sie auf ähnliche Weise eine Datenbindung für **Adresse**, **Telefonnummer**, **E-Mail**, **Beruf**, **Jahresgehalt (in Dollar)****undNein. von Feldern mit abhängigen Familienmitgliedern** mit den JSON-Schemaentitäten.

1. Wählen Sie das konvertierte **Beispiel-Kreditantragsformular** erneut aus, das im **[!UICONTROL output]** Ordner verfügbar ist, und wählen Sie **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Musterdatendatei herunterladen</br>

   [Datei laden](assets/json_data_file.txt)</br>

1. Ändern Sie bei Bedarf die Feldwerte und senden Sie das adaptive Formular. Die gesendeten Daten sind im CRX-Repository unter folgendem Speicherort verfügbar:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### XSD-Schema als Datenquelle verwenden {#xsddatasource}

**** Verwendungsfall: Sie erstellen ein adaptives Formular ohne Datenbindung mit dem Konvertierungsdienst für automatisierte Formulare und konfigurieren das XSD-Schema als Datenquelle. Sie binden die Felder des adaptiven Formulars manuell an das XSD-Schema und verwenden die **Vorschau mit Daten** , um Feldwerte im Voraus auszufüllen. Ändern Sie bei Bedarf die Feldwerte und senden Sie Daten an das CRX-Repository.

Bevor Sie den Anwendungsfall ausführen, stellen Sie sicher, dass Sie über Folgendes verfügen:

* [ein gültiges XSD-Schema, das mit der XML-Schemastruktur konform ist](#prepare-data-for-form-model)
* [ein adaptives Formular ohne Datenbindung](#generate-adaptive-forms-with-no-data-binding)

Führen Sie die folgenden Schritte aus:

1. Wählen Sie das konvertierte **Beispiel-Kreditantragsformular** aus, das im **[!UICONTROL output]** Ordner verfügbar ist, und tippen Sie auf **[!UICONTROL Properties]**.
1. Tippen Sie auf die **[!UICONTROL Form Model]** Registerkarte, wählen Sie **[!UICONTROL Schema]** aus der **[!UICONTROL Select From]** Dropdown-Liste und tippen Sie auf **[!UICONTROL Select Schema]** , um das im lokalen Dateisystem gespeicherte **Anwendungs-XSD-Schema** hochzuladen. Wählen Sie das Stammelement für das XSD-Schema aus und tippen Sie auf , **[!UICONTROL Save & Close]** um das Formular zu speichern.
1. Wählen Sie das **Beispiel-Kreditantragsformular** aus und tippen Sie auf **[!UICONTROL Edit]**.
1. Tippen Sie auf das Textfeld &quot;Name des Antragstellers&quot;und wählen Sie das ![Symbol](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) &quot;Konfigurieren&quot;.
Wählen Sie im Feld &quot;Bindungsreferenz&quot; **Bewerber** > **Name** und tippen Sie auf ![Fertiges Symbol](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) , um die Eigenschaften zu speichern. Erstellen Sie auf ähnliche Weise eine Datenbindung für **Adresse**, **Telefonnummer**, **E-Mail**, **Beruf**, **Jahresgehalt (in Dollar)****undNein. von Feldern mit abhängigen Familienmitgliedern** mit den XSD-Schemaentitäten.

1. Wählen Sie erneut das konvertierte **Beispiel-Kreditantragsformular** aus, das im Ordner &quot; **output** &quot;verfügbar ist, und wählen Sie **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Musterdatendatei herunterladen</br>

   [Datei laden](assets/loan-application-data-xml-data.zip)</br>


1. Ändern Sie bei Bedarf die Feldwerte und senden Sie das adaptive Formular. Die gesendeten Daten sind im CRX-Repository unter folgendem Speicherort verfügbar:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Erstellen adaptiver Formulare mit JSON-Bindung {#generate-adaptive-forms-with-json-binding}

Verwenden Sie den [automatisierten Forms-Konvertierungsdienst, um das ](convert-existing-forms-to-adaptive-forms.md)Beispiel-Kreditantragsformular[ in ein adaptives Formular mit Datenbindung zu konvertieren](#sample-adaptive-form) . Stellen Sie sicher, dass Sie das **[!UICONTROL Generate adaptive form(s) without data bindings]** Kontrollkästchen beim Generieren des adaptiven Formulars nicht aktivieren.

![Adaptives Formular mit JSON-Bindung](assets/generate_af_with_data_bindings.png)

### JSON-Schema als Datenquelle verwenden {#jsonwithdatabinding}

**** Verwendungsfall: Sie erstellen ein adaptives Formular mit JSON-Datenbindung mithilfe des Dienstes &quot;Automatisierte Formularkonvertierung&quot;. Die Funktion zum Vorausfüllen und zum Senden von Formularen ist nahtlos verfügbar. Sie benötigen keine Konfigurationsschritte.

Bevor Sie den Anwendungsfall ausführen, stellen Sie sicher, dass Sie über [ein adaptives Formular mit Datenbindung](#generate-adaptive-forms-with-json-binding)verfügen.

Führen Sie die folgenden Schritte aus:

1. Wählen Sie das konvertierte **Beispiel-Kreditantragsformular** erneut aus, das im **[!UICONTROL output]** Ordner verfügbar ist, und wählen Sie **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Musterdatendatei herunterladen</br>

   [Datei laden](assets/loan_application_data_source_json_data_binding.txt)</br>

1. Ändern Sie bei Bedarf die Feldwerte und senden Sie das adaptive Formular. Die gesendeten Daten sind im CRX-Repository unter folgendem Speicherort verfügbar:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## JSON-Daten für übermittelte adaptive Formulare in XML-Format konvertieren {#convert-submitted-adaptive-form-data-to-xml}

Wenn Sie Werte in adaptive Formularfelder eingeben und diese senden, sind die Daten im JSON-Format im CRX-Repository verfügbar. Sie können das Format der JSON-Daten entweder mit der [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) -API oder dem folgenden Beispielcode in XML konvertieren:

```
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;
import org.apache.sling.commons.json.xml.XML;
 
public class ConversionUtils {
 
    public static String jsonToXML(String jsonString) throws JSONException {
        //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
        //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
        //Note: Need to extract boundData part before converting to XML
        return XML.toString(new JSONObject(jsonString));
    }
}
```
