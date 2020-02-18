---
title: Erweitern des standardmäßigen Meta-Modells
seo-title: Erweitern des standardmäßigen Meta-Modells
description: Erweitern Sie das Standard-Metadatenmodell, um für Ihr Unternehmen spezifische Muster, Überprüfungen und Entitäten hinzuzufügen und Konfigurationen auf adaptive Formularfelder anzuwenden, während der Dienst für die automatisierte Formularkonvertierung ausgeführt wird.
seo-description: Erweitern Sie das Standard-Metadatenmodell, um für Ihr Unternehmen spezifische Muster, Überprüfungen und Entitäten hinzuzufügen und Konfigurationen auf adaptive Formularfelder anzuwenden, während der Dienst für die automatisierte Formularkonvertierung ausgeführt wird.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: 5d4dba8fea7439b991a7a15872e6f4ed48156ac9

---


# Erweitern des standardmäßigen Meta-Modells {#extend-the-default-meta-model}

Der Dienst &quot;Automatisierte Formularkonvertierung&quot;identifiziert und extrahiert Formularobjekte aus Quellformularen. Die semantische Zuordnung hilft dem Dienst bei der Entscheidung, wie die extrahierten Objekte in einem adaptiven Formular dargestellt werden. Ein Quellformular kann beispielsweise viele verschiedene Arten von Darstellungen eines Datums aufweisen. Die semantische Zuordnung hilft, alle Darstellungen von Datumsformularobjekten des Quellformulars mit der Datumskomponente der adaptiven Formulare zu verknüpfen. Mit der semantischen Zuordnung kann der Dienst außerdem während der Konvertierung Überprüfungen, Regeln, Datenmuster, Hilfetext und Barrierefreiheitseigenschaften vorkonfigurieren und auf adaptive Formularkomponenten anwenden.

![](assets/meta-model.gif)

Meta-Modell ist ein JSON-Schema. Bevor Sie mit dem Meta-Modell beginnen, stellen Sie sicher, dass Sie mit JSON gut vertraut sind. Sie müssen über Erfahrung beim Erstellen, Bearbeiten und Lesen von im JSON-Format gespeicherten Daten verfügen.

## Standard-Meta-Modell {#default-meta-model}

Der Dienst für die automatisierte Formularkonvertierung verfügt über ein Standard-Meta-Modell. Es handelt sich um ein JSON-Schema und befindet sich in der Adobe Cloud mit anderen Komponenten des Automatisierten Forms-Konvertierungsdiensts. Eine Kopie des Meta-Modells finden Sie auf Ihrem lokalen AEM-Server unter:

http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json.

Das Schema des Meta-Modells wird von Schemaentitäten unter https://schema.org/docs/schemas.html abgeleitet. Es enthält Personen, PostalAddress, LocalBusiness und weitere Entitäten, wie in https://schema.org definiert. Jede Entität des Meta-Modells entspricht dem JSON-Schemaobjekttyp. Der folgende Code stellt eine Beispiel-Meta-Modellstruktur dar:

```
   "Entity": {
      "id": "Entity",
      "properties": {
        "name": {
          "type": "string"
        },

        "description": {
          "type": "string",
          "description": "Description of the item"
        }
      }
    }
```

## Herunterladen des standardmäßigen Meta-Modells {#download-the-default-meta-model}

Führen Sie die folgenden Schritte aus, um das standardmäßige Meta-Modell in das lokale Dateisystem herunterzuladen:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
1. Navigieren Sie zum Ordner **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** >**** **[!UICONTROL Meta Model]**.
1. Wählen Sie die **[!UICONTROL global.schema.json]** Datei aus und tippen Sie auf **[!UICONTROL Download]**. Ein Dialogfeld zum Herunterladen wird angezeigt. Select the **[!UICONTROL Download asset(s) as binary files]** option. Tippen Sie auf **[!UICONTROL Download]**. Ein Archiv wird heruntergeladen.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## Das Meta-Modell {#understanding-the-meta-model}

Ein Meta-Modell bezieht sich auf eine JSON-Schemadatei, die Entitäten enthält. Alle Entitäten in der JSON-Schemadatei enthalten einen Namen und eine ID. Jede Entität kann mehrere Eigenschaften enthalten. Die Entitäten und ihre Eigenschaften können je nach Domäne variieren. Sie können eine Schemadatei mit Suchbegriffen und Feldkonfigurationen erweitern, um Schemaeigenschaften adaptiven Formularkomponenten zuzuordnen.

```
"Event": {
      "id": "Eventid",
      "allOf": [
        {
          "$ref": "#Entity"
        },
        {
          "properties": {
            "startDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the start date and time of the event in ISO 8601 date format."
            },
            "endDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the end date and time of the event in ISO 8601 date format."
            },
            "location": {
              "$ref": "#PostalAddress",
              "description": "Specify the location of the event."
            }
          }
        }
      ]
    }
```

In diesem Beispiel stellt **Event** den Namen einer Entität mit einem Wert für **id** als **Eventid** dar. Die Ereignisentität umfasst mehrere Eigenschaften:

* startDate
* endDate
* location

Das **allOf** -Konstrukt im Meta-Modell ermöglicht die Vererbung zwischen Entitäten.

Jede Eigenschaft kann außerdem Folgendes umfassen:

* [JSON-Schemaeigenschaften](#jsonschemaproperties)
* [Suchbegriffbasierte Suche, um Eigenschaften auf erstellte adaptive Formularfelder anzuwenden](#keywordsearch)
* [Zusätzliche Eigenschaften](#additionalproperties)

![Eigenschaften von Metamodellen](assets/meta_model_elements.gif)

Auf der Grundlage der mit **aem:affKeyword** referenzierten Suchbegriffe führt der Konvertierungsdienst eine Suche in den Quellformularfeldern durch. Der Konvertierungsdienst wendet die JSON-Schemaeigenschaften und zusätzliche Eigenschaften auf die Felder an, die die Suchkriterien erfüllen.

In diesem Beispiel sucht der Konvertierungsdienst im Quellformular nach den Schlüsselwörtern Telefon, Telefon, Handy, Handy, Handy, Heimtelefon, Telefonnummer und Telefonnummer. Basierend auf den Feldern, die diese Suchbegriffe enthalten, wendet der Konvertierungsdienst den Typ, das Muster und aem:afProperties nach der Konvertierung auf die Felder des adaptiven Formulars an.

### JSON-Schemaeigenschaften für erstellte adaptive Formularfelder {#jsonschemaproperties}

Das Meta-Modell unterstützt die folgenden allgemeinen Eigenschaften des JSON-Schemas für adaptive Formularfelder, die mit dem Automatisierten Forms-Konvertierungsdienst generiert wurden:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Eigenschaftsname</strong></th> 
   <th><strong>Beschreibung</strong></th> 
  </tr> 
  <tr> 
   <td><p>Titels</p></td> 
   <td> 
    <p>Der in der Eigenschaft title in einem Meta-Modell erwähnte Text dient als Suchbegriff, um Aktionen in den erstellten Feldern des adaptiven Formulars durchzuführen. Ändern Sie beispielsweise die Beschriftung eines adaptiven Formularfelds. Weitere Informationen finden Sie unter <strong>Ändern der Beschriftung eines Formularfelds</strong> in den Beispielen für <a href="#custommetamodelexamples">benutzerdefiniertes Meta-Modell.</a></p> </td> 
  </tr>
  <td><p>description</p></td> 
   <td> 
    <p>Die Eigenschaft description legt den Hilfetext für das generierte adaptive Formularfeld fest. Weitere Informationen finden Sie unter <strong>Hilfetext zu einem Formularfeld</strong> hinzufügen in Beispielen für <a href="#custommetamodelexamples">benutzerspezifische Meta-Modelle.</a></p> </td> 
  </tr>
  <td><p>type</p></td> 
   <td> 
    <p>Die type-Eigenschaft definiert den Datentyp für das generierte adaptive Formularfeld. Die möglichen Werte für die Eigenschaft title umfassen:</p>
    <ul> 
     <li>Zeichenfolge: Generiert ein Feld für ein adaptives Formular des Textdatentyps.</li> 
     <li>Nummer: Generiert ein adaptives Formularfeld des numerischen Datentyps.</li>
     <li>integer: Generiert ein adaptives Formularfeld des numerischen Datentyps mit dem Untertyp "integer".</li>
     <li>boolean: Generiert eine Komponente des adaptiven Formulars zum Wechseln.</li>
     </ul><p>Weitere Informationen zur Verwendung der type-Eigenschaft in einem Meta-Modell finden Sie unter <strong>Ändern des Typs eines Formularfelds</strong> in Beispielen für <a href="#custommetamodelexamples">benutzerspezifische Meta-Modelle.</a></p></td> 
  </tr>
  <td><p>pattern</p></td> 
   <td> 
    <p>Die pattern-Eigenschaft schränkt den Wert für das generierte adaptive Formularfeld basierend auf einem regulären Ausdruck ein. Beispielsweise beschränkt der folgende Code im Meta-Modell den Wert für das erstellte adaptive Formularfeld auf zehn Stellen:<br>"pattern": "/\\d{10}/"<br>Entsprechend beschränkt der folgende Code im Meta-Modell den Wert eines Felds auf ein bestimmtes Datumsformat.<br> "pattern": "date{DD MMMM, YYYY}",</p> </td> 
  </tr>
  <td><p>format</p></td> 
   <td> 
    <p>Die format-Eigenschaft schränkt den Wert für das generierte adaptive Formularfeld basierend auf einem benannten Muster anstelle eines regulären Ausdrucks ein. Die möglichen Werte für die format-Eigenschaft umfassen:<ul><li>email: Erstellt eine Komponente für ein adaptives E-Mail-Formular.</li><li>hostname: Erstellt eine Komponente des adaptiven Textfelds.</li></ul>Weitere Informationen zur Verwendung der format-Eigenschaft in einem Meta-Modell finden Sie unter <strong>Ändern des Formats eines Formularfelds</strong> in Beispielen für <a href="#custommetamodelexamples">benutzerspezifische Meta-Modelle.</a></p> </td> 
  </tr>
  <td><p>enum und enumNames</p></td> 
   <td> 
    <p>Die Eigenschaften enum und enumNames beschränken die Werte von Dropdown-, Kontrollkästchen- oder Optionsfeldern auf einen festen Satz. Die in enumNames aufgeführten Werte werden auf der Benutzeroberfläche angezeigt. Die mit der enum-Eigenschaft aufgelisteten Werte werden für die Berechnung verwendet.<br>Weitere Informationen finden Sie unter <strong>Konvertieren eines Formularfelds in Kontrollkästchen mit mehreren Optionen im adaptiven Formular</strong>, <strong>Konvertieren eines Textfelds in eine Dropdown-Liste im adaptiven Formular</strong>und <strong>Hinzufügen zusätzlicher Optionen zur Dropdownliste</strong> in Beispielen für <a href="#custommetamodelexamples">benutzerspezifische Metadatenmodelle.</a></p> </td> 
  </tr>
 </tbody> 
</table>

### Suchbegriffbasierte Suche, um Eigenschaften auf erstellte adaptive Formularfelder anzuwenden {#keywordsearch}

Der Automatisierte Forms-Konvertierungsdienst führt während der Konvertierung eine Suchbegriffsuche im Quellformular durch. Nach dem Filtern der Felder, die die Suchkriterien erfüllen, wendet der Konvertierungsdienst die für diese Felder im Metadatenmodell definierten Eigenschaften auf die generierten adaptiven Formularfelder an.

Auf Suchbegriffe wird mithilfe der **Eigenschaft aem:affKeyword** verwiesen.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

In diesem Beispiel verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchbegriff. Nach dem Abrufen des Textes für die **Bankkontonummer** im Formular wandelt der Konvertierungsdienst das Feld mithilfe der **type** -Eigenschaft in einen **Zahlentyp** um.

### Zusätzliche Eigenschaften für erstellte adaptive Formularfelder {#additionalproperties}

Sie können die Eigenschaft **aem:afProperties** im Meta-Modell verwenden, um die folgenden zusätzlichen Eigenschaften für Felder in adaptiven Formularen zu definieren, die mit dem Automatisierten Forms-Konvertierungsdienst generiert wurden:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Eigenschaftsname</strong></th> 
   <th><strong>Beschreibung</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiLine</p></td> 
   <td> 
    <p>Die multiline-Eigenschaft konvertiert ein Quellformularfeld nach der Konvertierung in ein mehrzeiliges Feld im adaptiven Formular. Weitere Informationen finden Sie unter <strong>Konvertieren eines Zeichenfolgenfelds in ein mehrzeiliges Feld</strong> in Beispielen für <a href="#custommetamodelexamples">benutzerspezifische Meta-Modelle.</a></p> </td> 
  </tr>
  <td><p>obligatorisch</p></td> 
   <td> 
    <p>Die obligatorische Eigenschaft legt die Eingabe für ein adaptives Formularfeld nach der Konvertierung als obligatorisch fest.<br>Weitere Informationen finden Sie unter <strong>Hinzufügen von Überprüfungen zu Feldern</strong> in adaptiven Formularen in Beispielen für <a href="#custommetamodelexamples">benutzerspezifische Meta-Modelle.</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>Mit der Eigenschaft jcr:title und der JSON-Schemaeigenschaft können Sie die Beschriftung eines adaptiven Formularfelds nach der Konvertierung ändern.<br>Weitere Informationen finden Sie unter <strong>Ändern der Beschriftung eines Formularfelds</strong> in den Beispielen für <a href="#custommetamodelexamples">benutzerdefiniertes Meta-Modell.</a><br>Informationen zu weiteren Eigenschaften, die Sie mithilfe des JSON-Schemas auf adaptive Formularfelder anwenden können, finden Sie unter <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">Erstellen adaptiver Formulare mit dem JSON-Schema</a> .</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType und guideNodeClass</p></td> 
   <td> 
    <p>sling:resourceType- und guideNodeClass-Eigenschaften ermöglichen es Ihnen, ein Formularfeld einer entsprechenden adaptiven Formularkomponente zuzuordnen.<br>Weitere Informationen finden Sie unter <strong>Konvertieren eines Formularfelds in Kontrollkästchen mit mehreren Auswahlmöglichkeiten im adaptiven Formular</strong> und <strong>Konvertieren eines Textfelds in eine Dropdown-Liste im adaptiven Formular</strong> in Beispielen für <a href="#custommetamodelexamples">benutzerspezifische Metadatenmodelle.</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>Die validatePictureClause-Eigenschaft legt eine Überprüfung des Formats fest, das im Feld für das adaptive Formular nach der Konvertierung zulässig ist.<br>Weitere Informationen finden Sie unter <strong>Hinzufügen von Überprüfungen zu Feldern</strong> in adaptiven Formularen in Beispielen für <a href="#custommetamodelexamples">benutzerspezifische Meta-Modelle.</p> </td> 
  </tr>
 </tbody> 
</table>

## Ändern von Feldern in adaptiven Formularen mit benutzerdefiniertem Meta-Modell {#modify-adaptive-form-fields-using-custom-meta-model}

Ihr Unternehmen kann Muster und Überprüfungen zusätzlich zu den im Standard-Meta-Modell aufgeführten aufweisen. Sie können das standardmäßige Metamodell erweitern, um Muster, Überprüfungen und Entitäten hinzuzufügen, die für Ihr Unternehmen spezifisch sind. Der Dienst &quot;Automatisierte Formularkonvertierung&quot;wendet das benutzerdefinierte Metadatenmodell bei der Konvertierung auf die Formularfelder an. Sie können das Meta-Modell weiter aktualisieren, wenn neue, unternehmensspezifische Muster, Überprüfungen und Entitäten erkannt werden.

Der Dienst &quot;Automatisierte Formularkonvertierung&quot;verwendet ein Standardmeta-Modell, das am folgenden Speicherort gespeichert wurde, um den Feldern des adaptiven Formulars während der Konvertierung Quellformulare zuzuordnen:

http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

Sie können jedoch ein benutzerdefiniertes Meta-Modell in einem Ordner speichern und die Konvertierungsdiensteigenschaften ändern, um das benutzerdefinierte Meta-Modell während der Konvertierung zu verwenden.

### Verwenden Sie benutzerdefiniertes Meta-Modell während der Konvertierung {#use-custom-meta-model-during-conversion}

Führen Sie die folgenden Schritte aus, um während der Konvertierung ein benutzerdefiniertes Meta-Modell zu verwenden:

1. Erstellen Sie einen Ordner unter **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** und laden Sie die benutzerdefinierte JSON-Schemadatei für das Metadatenmodell in den Ordner hoch.
1. Öffnen Sie die Eigenschaften des Konvertierungsdiensts mit:

   **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]**> **&lt;** Eigenschaften der ausgewählten Konfiguration **>**

1. Geben Sie auf der **[!UICONTROL Basic]** Registerkarte die Position des benutzerdefinierten Meta-Modells im Feld ein und **[!UICONTROL Custom Meta-model]** tippen Sie auf **[!UICONTROL Save & Close]**.
1. [Führen Sie die Konvertierung](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) aus, um das benutzerdefinierte Meta-Modell auf den Konvertierungsprozess anzuwenden.

### Beispiele für benutzerspezifische Meta-Modelle {#custommetamodelexamples}

Einige gängige Beispiele für die Verwendung eines benutzerdefinierten Meta-Modells zum Ändern der Feldeigenschaften eines adaptiven Formulars sind:

* Ändern der Beschriftung eines Formularfelds
* Ändern des Formularfeldtyps
* Hinzufügen von Hilfetext zu einem Formularfeld
* Konvertieren eines Formularfelds in Optionsfelder mit mehreren Auswahlmöglichkeiten im adaptiven Formular
* Format eines Formularfelds ändern
* Hinzufügen von Überprüfungen zu Feldern in adaptiven Formularen
* Konvertieren eines Formularfelds in Dropdown-Listenoptionen im adaptiven Formular
* Hinzufügen zusätzlicher Optionen zur Dropdownliste
* Konvertieren eines Zeichenfolgenfelds in ein mehrzeiliges Feld

#### Ändern der Beschriftung eines Formularfelds {#modify-the-label-of-a-form-field}

**** Beispiel: Ändern Sie die Bezeichnung der Kontonummer im Formular nach der Konversion in Benutzerdefinierte Kontonummer im adaptiven Formular.

In diesem benutzerdefinierten Meta-Modell verwendet der Konvertierungsdienst die **title** -Eigenschaft als Suchbegriff. Nach dem Abrufen des Textes der **Bankkontonummer** im Formular ersetzt der Konvertierungsdienst den Text durch die **Kundenkontonummer** -Zeichenfolge, die im Abschnitt **aem:afProperties** mit der Eigenschaft **jcr:title** angegeben ist.

```
{
  "numberfields": {
      "type": "number",
   "title": "Bank account number",
   "aem:afProperties" : {
    "jcr:title" : "Customer account number"
   }
   }
}
```

#### Ändern des Formularfeldtyps {#modify-the-type-of-a-form-field}

**Beispiel**: Ändern Sie das Feld für die **Kontonummer** des Texttyps im Formular, bevor Sie nach der Konvertierung in ein Feld für den Zahlentyp im adaptiven Formular konvertieren.

In diesem benutzerdefinierten Meta-Modell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchbegriff. Nach dem Abrufen des Textes für die **Bankkontonummer** im Formular wandelt der Konvertierungsdienst das Feld mithilfe der **type** -Eigenschaft in einen Zahlentyp um.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### Hinzufügen von Hilfetext zu einem Formularfeld {#add-help-text-to-a-form-field}

**Beispiel**: Fügen Sie dem Feld **Bankkontonummer** des adaptiven Formulars Hilfetext hinzu.

In diesem benutzerdefinierten Meta-Modell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchbegriff. Nach dem Abrufen des Textes für die **Bankkontonummer** im Formular fügt der Konvertierungsdienst dem Feld für das adaptive Formular den Hilfetext mithilfe der Eigenschaft **description** hinzu.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "description": "Specify your bank account number."
 }
}
```

#### Konvertieren eines Formularfelds in Kontrollkästchen mit mehreren Auswahlmöglichkeiten im adaptiven Formular {#convert-a-form-field-to-multiple-choice-check-boxes-in-the-adaptive-form}

**Beispiel**: Konvertieren Sie das Feld **Land** des Zeichenfolgentyps im Formular vor der Konvertierung in Kontrollkästchen im adaptiven Formular nach der Konvertierung.

In diesem benutzerdefinierten Meta-Modell verwendet der Konvertierungsdienst Text in **aem:affKeyword** als Suchbegriff. Nach dem Abrufen des **Ländertextes** im Formular wandelt der Konvertierungsdienst das Feld mithilfe der **enum** -Eigenschaft in folgende Kontrollkästchen um:

* Indien
* England
* Australien
* Neuseeland

**sling:resourceType** - und **guideNodeClass** -Eigenschaften ordnen ein Formularfeld der Komponente für das adaptive Kontrollkästchen zu.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### Format eines Formularfelds ändern {#modify-the-format-of-a-form-field}

**Beispiel**: Ändern Sie das Format des Felds &quot; **E-Mail-Adresse** &quot;in ein E-Mail-Format.

In diesem benutzerdefinierten Meta-Modell verwendet der Konvertierungsdienst Text in **aem:affKeyword** als Suchbegriff. Nach dem Abrufen des Textes für die **E-Mail-Adresse** im Formular konvertiert der Konvertierungsdienst das Feld mithilfe der **format** -Eigenschaft in ein E-Mail-Format.

```
{
   "additionalDetails" : {
      "aem:affKeyword": ["E-mail Address"],
       "type" : "string",
       "format" : "email"
  } 
}
```

#### Hinzufügen von Überprüfungen zu Feldern in adaptiven Formularen {#add-validations-to-adaptive-form-fields}

**** Beispiel 1: Fügen Sie dem Feld **Postleitzahl** des adaptiven Formulars eine Überprüfung hinzu.

In diesem benutzerspezifischen Meta-Modell verwendet der Konvertierungsdienst Text in **aem:affKeyword** als Suchbegriff. Nach dem Abrufen des **Postleitzahltextes** im Formular fügt der Konvertierungsdienst dem Feld eine Überprüfung mit der **Eigenschaft validatePictureClause** hinzu, die im Abschnitt **aem:afProperties** definiert ist. Auf der Grundlage der Überprüfung muss die Eingabe, die Sie nach der Konvertierung für das Feld **Postleitzahl** im adaptiven Formular angeben, sechs Zeichen umfassen.

```
{
   "postalCode" : {
      "aem:affKeyword": ["Postal Code"],
      "type" : "string",
      "aem:afProperties" : {
        "validatePictureClause" : "\\d{6}"
      } 
   }
}
```

**** Beispiel 2: Fügen Sie dem Feld **Bankkontonummer** des adaptiven Formulars eine Überprüfung hinzu.

In diesem benutzerspezifischen Meta-Modell verwendet der Konvertierungsdienst Text in **aem:affKeyword** als Suchbegriff. Nachdem der Text für die **Kontonummer** im Formular abgerufen wurde, fügt der Konvertierungsdienst dem Feld eine Überprüfung mit der **obligatorischen** Eigenschaft hinzu, die im Abschnitt **aem:afProperties** definiert ist. Basierend auf der Validierung müssen Sie einen Wert für das Feld **Kontonummer** angeben, bevor Sie das Formular nach der Konvertierung übermitteln.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "aem:afProperties" : {
        "mandatory": "true"
      }   
   }
}
```

#### Textfeld in Dropdown-Liste im adaptiven Formular konvertieren {#convert-a-text-field-to-drop-down-list-in-the-adaptive-form}

**Beispiel**: Konvertieren Sie das Feld **Land** des Zeichenfolgentyps im Formular vor der Konvertierung in Dropdown-Optionen im adaptiven Formular nach der Konvertierung.

In diesem benutzerspezifischen Meta-Modell verwendet der Konvertierungsdienst Text in **aem:affKeyword** als Suchbegriff. Nach dem Abrufen des **Ländertextes** im Formular konvertiert der Konvertierungsdienst das Feld mithilfe der **enum** -Eigenschaft in die folgenden Dropdown-Listenoptionen:

* Indien
* England
* Australien
* Neuseeland

**sling:resourceType** - und **guideNodeClass** -Eigenschaften ordnen ein Formularfeld der Dropdown-Komponente des adaptiven Formulars zu.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidedropdownlist",
      "guideNodeClass": "guideDropDownlist"
    }
  }
}
```

#### Hinzufügen zusätzlicher Optionen zur Dropdownliste {#add-additional-options-to-the-drop-down-list}

**** Beispiel: Fügen Sie **Sri Lanka** als zusätzliche Option zu einer vorhandenen Dropdown-Liste hinzu, indem Sie ein benutzerdefiniertes Meta-Modell verwenden.

Um eine zusätzliche Option hinzuzufügen, aktualisieren Sie die **enum** -Eigenschaft mit der neuen Option. In diesem Beispiel aktualisieren Sie die **enum** -Eigenschaft mit **Sri Lanka** als zusätzliche Option. Die in der **Enum** -Eigenschaft aufgelisteten Werte werden in der Dropdownliste angezeigt.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand",
   "Sri Lanka"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### Konvertieren eines Zeichenfolgenfelds in ein mehrzeiliges Feld {#convert-a-string-field-to-a-multi-line-field}

**** Beispiel: Konvertieren Sie das Feld **Adresse** des Zeichenfolgentyps nach der Konvertierung in ein mehrzeiliges Feld im Formular.

In diesem benutzerspezifischen Meta-Modell verwendet der Konvertierungsdienst Text in **aem:affKeyword** als Suchbegriff. Nach dem Abrufen des **Adresstexts** im Formular wandelt der Dienst das Textfeld mithilfe der **mehrzeiligen** Eigenschaft, die im Abschnitt **aem:afProperties** definiert ist, in ein mehrzeiliges Feld um.

```
{
 "multiline" : {
   "aem:affKeyword": [
      "Address"
    ],
    "type" : "string",
    "aem:afProperties": {
      "multiline": "true"
    }
  }
}
```
