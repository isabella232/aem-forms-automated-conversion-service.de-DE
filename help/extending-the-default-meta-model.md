---
title: Erweitern des Standardmetamodells
seo-title: Extend the default meta-model
description: Erweitern Sie das Standard-Metamodell, um Muster, Validierungen und Entitäten hinzuzufügen, die für Ihre Organisation spezifisch sind, und Konfigurationen auf adaptive Formularfelder anzuwenden, während Sie den Dienst für die automatische Formularkonvertierung ausführen.
seo-description: Extend the default meta-model to add pattern, validations, and entities specific to your organization and apply configurations to adaptive form fields while running the Automated Forms Conversion service.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
exl-id: f679059c-18aa-4cb5-8368-ed27e96c20de
source-git-commit: e3ba3807668084495acb77f57ea2da6d5a53e626
workflow-type: ht
source-wordcount: '2594'
ht-degree: 100%

---

# Erweitern des Standardmetamodells {#extend-the-default-meta-model}

Der Dienst zur automatischen Formularkonvertierung identifiziert und extrahiert Formularobjekte aus Quellformularen. Semantic Mapper hilft dem Dienst zu entscheiden, wie die extrahierten Objekte in einem adaptiven Formular dargestellt werden. Beispielsweise kann ein Quellformular viele verschiedene Arten von Darstellungen eines Datums enthalten. Der Semantic Mapper hilft dabei, alle Darstellungen von Datumsformularobjekten des Quellformulars der Datumskomponente der adaptiven Formulare zuzuordnen. Mit Semantic Mapper kann der Dienst auch Validierungen, Regeln, Datenmuster, Hilfetexte und Eingabehilfeeigenschaften während der Konvertierung vorkonfigurieren und auf adaptive Formularkomponenten anwenden.

![](assets/meta-model.gif)

Das Metamodell ist ein JSON-Schema. Bevor Sie mit dem Metamodell beginnen, stellen Sie sicher, dass Sie mit JSON vertraut sind. Sie müssen Erfahrung im Erstellen, Bearbeiten und Lesen von Daten haben, die im JSON-Format gespeichert sind.

## Standardmetamodell {#default-meta-model}

Im Dienst für die automatische Formularkonvertierung ist ein Standardmetamodell verfügbar. Dies ist ein JSON-Schema und befindet sich zusammen mit anderen Komponenten des Dienstes für die automatische Formularkonvertierung in Adobe Cloud. Eine Kopie des Metamodells finden Sie auf Ihrem lokalen AEM-Server unter:  http://&lt;Server>:&lt;Port>/aem/forms.html/content/dam/formsanddocuments/metamodel/`global.schema.json`. Sie können auch hier [klicken](assets/en.globalschema.json), um auf das englische Schema zuzugreifen oder es herunterzuladen. Das Metamodell für die Sprachen [Französisch](assets/fr.globalschema.json), [Deutsch](assets/de.globalschema.json) [Spanisch](assets/es.globalschema.json), [Italienisch](assets/it.globalschema.json) und [Portugiesisch](assets/pt_br.globalschema.json) kann ebenfalls heruntergeladen werden.

Das Schema des Metamodells wird von Schemaentitäten unter https://schema.org/docs/schemas.html abgeleitet. Es enthält Person, PostalAddress, LocalBusiness und weitere Entitäten, wie auf https://schema.org definiert. Jede Entität des Metamodells entspricht dem JSON-Schemaobjekttyp. Der folgende Code zeigt eine Beispiel-Metamodellstruktur:

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

## Herunterladen des Standardmetamodells {#download-the-default-meta-model}

Führen Sie die folgenden Schritte aus, um das Standardmetamodell in das lokale Dateisystem herunterzuladen:

1. Melden Sie sich bei Ihrer AEM Forms-Instanz an.
1. Navigieren Sie zum Ordner **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** **>** **[!UICONTROL Metamodel]**.
1. Wählen Sie die Datei **[!UICONTROL global.schema.json]** aus und tippen Sie auf **[!UICONTROL Herunterladen]**. Das Dialogfeld zum Herunterladen wird angezeigt. Wählen Sie die Option **[!UICONTROL Asset(s) als Binärdateien herunterladen]**. Tippen Sie auf **[!UICONTROL Herunterladen]**. Ein Archiv wird heruntergeladen.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## Grundlagen des Metamodells {#understanding-the-meta-model}

Ein Metamodell bezieht sich auf eine JSON-Schemadatei, die Entitäten enthält. Alle Entitäten in der JSON-Schemadatei enthalten einen Namen und eine ID. Jede Entität kann mehrere Eigenschaften enthalten. Die Entitäten und ihre Eigenschaften können je nach Domäne variieren. Sie können eine Schemadatei mit Schlüsselwörtern und Feldkonfigurationen erweitern, um Schemaeigenschaften adaptiven Formularkomponenten zuzuordnen.

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

In diesem Beispiel repräsentiert **Ereignis** den Namen einer Entität mit einem Wert für **id** als **Eventid**. Die Ereignisentität enthält mehrere Eigenschaften:

* startDate
* endDate
* location

Das Konstrukt **allOf** im Metamodell ermöglicht die Vererbung zwischen Entitäten.

Jede Eigenschaft kann ferner Folgendes umfassen:

* [JSON-Schema-Eigenschaften](#jsonschemaproperties)
* [Schlüsselwortbasierte Suche zum Anwenden von Eigenschaften auf Felder im generierten adaptiven Formular](#keywordsearch)
* [Zusätzliche Eigenschaften](#additionalproperties)

![Eigenschaften des Metamodells](assets/meta_model_elements.gif)

Basierend auf den Schlüsselwörtern, auf die mit **aem:affKeyword** verwiesen wird, führt der Konvertierungsdienst eine Suchoperation für die Quellformularfelder durch. Der Konvertierungsdienst wendet die Eigenschaften des JSON-Schemas und zusätzliche Eigenschaften auf die Felder an, die die Suchkriterien erfüllen.

In diesem Beispiel sucht der Konvertierungsdienst im Quellformular nach den Schlüsselwörtern Tel., Telefon geschäftlich, Telefon privat, Mobiltelefon, Telefon, Handy, Telefonnr., Nummer und Telefonnummer. Basierend auf den Feldern, die diese Schlüsselwörter enthalten, wendet der Konvertierungsdienst nach der Konvertierung den Typ, das Muster und aem:afProperties auf die Felder des adaptiven Formulars an.

### JSON-Schemaeigenschaften für generierte adaptive Formularfelder {#jsonschemaproperties}

Das Metamodell unterstützt die folgenden allgemeinen Eigenschaften des JSON-Schemas für Felder in adaptiven Formularen, die mit dem Dienst für die automatische Formularkonvertierung generiert wurden:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Eigenschaftsname</strong></th> 
   <th><strong>Beschreibung</strong></th> 
  </tr> 
  <tr> 
   <td><p>Titel</p></td> 
   <td> 
    <p>Der in der Titeleigenschaft in einem Metamodell erwähnte Text dient als Suchschlüsselwort, um Aktionen für die Felder des generierten adaptiven Formulars auszuführen. Beispiel: Ändern der Beschriftung eines Feldes in einem adaptiven Formular. Weitere Informationen finden Sie unter <strong>Ändern der Beschriftung eines Formularfelds</strong> in <a href="#custommetamodelexamples">Beispiele für benutzerdefinierte Metamodelle.</a></p> </td> 
  </tr>
  <td><p>Beschreibung</p></td> 
   <td> 
    <p>Die Eigenschaft „description“ legt den Hilfetext für das Feld im generierten adaptiven Formular fest. Weitere Informationen finden Sie unter <strong>Hilfetext zu einem Formularfeld hinzufügen</strong> unter <a href="#custommetamodelexamples">Beispiele für benutzerdefinierte Metamodelle.</a></p> </td> 
  </tr>
  <td><p>type</p></td> 
   <td> 
    <p>Die Eigenschaft „type“ definiert den Datentyp für das Feld im generierten adaptiven Formular. Die möglichen Werte für die Eigenschaft „title“ umfassen:</p>
    <ul> 
     <li>string: Erzeugt ein Feld mit dem Datentyp „text“ im adaptiven Formular.</li> 
     <li>number: Erzeugt ein Feld des numerischen Datentyps im adaptiven Formular.</li>
     <li>integer: Erzeugt ein Feld vom numerischen Datentyp mit dem Untertyp „integer“ im adaptiven Formular.</li>
     <li>Boolescher Wert: adaptive Formularkomponente des Typs „Switch“.</li>
     </ul><p>Weitere Informationen zur Verwendung der type-Eigenschaft in einem Metamodell finden Sie unter <strong>Ändern des Typs eines Formularfelds</strong> in <a href="#custommetamodelexamples">Beispiele für benutzerdefinierte Metamodelle.</a></p></td> 
  </tr>
  <td><p>pattern</p></td> 
   <td> 
    <p>Die pattern-Eigenschaft beschränkt den Wert für das Feld im generierten adaptiven Formular basierend auf einem regulären Ausdruck. Beispielsweise beschränkt der folgende Code im Metamodell den Wert für das Feld im generierten adaptiven Formular auf zehn Stellen: <br>"pattern": "/\\d{10}/"<br> Ebenso beschränkt der folgende Code im Metamodell den Wert eines Feldes auf ein bestimmtes Datumsformat.<br> "pattern": "date{DD MMMM, YYYY}",</p> </td> 
  </tr>
  <td><p>format</p></td> 
   <td> 
    <p>Die Formateigenschaft beschränkt den Wert für das Feld im generierten adaptiven Formular basierend auf einem benannten Muster anstelle eines regulären Ausdrucks. Die möglichen Werte für die Eigenschaft „format“ umfassen:<ul><li>email: Erzeugt eine adaptive Formularkomponente für E-Mail-Adressen.</li><li>hostname: Erzeugt eine adaptive Formularkomponente für ein Textfeld.</li></ul>Weitere Informationen zur Verwendung der format-Eigenschaft in einem Metamodell finden Sie unter <strong>Ändern des Formats eines Formularfelds</strong> in <a href="#custommetamodelexamples">Beispiele für benutzerdefinierte Metamodelle.</a></p> </td> 
  </tr>
  <td><p>enum und enumNames</p></td> 
   <td> 
    <p>Die Eigenschaften „enum“ und „enumNames“ beschränken die Werte von Dropdown-, Kontrollkästchen- oder Optionsfeldfeldern auf einen festen Satz. In „enumNames“ aufgelistete Werte werden in der Benutzeroberfläche angezeigt. Die mit der Eigenschaft „enum“ aufgelisteten Werte werden zur Berechnung verwendet.<br>Weitere Informationen finden Sie unter <strong>Konvertieren eines Formularfelds in Multiple-Choice-Kontrollkästchen im adaptiven Formular</strong>, <strong>Konvertieren eines Textfelds in eine Dropdown-Liste im adaptiven Formular</strong> und <strong>Hinzufügen zusätzlicher Optionen zur Dropdown-Liste</strong> in <a href="#custommetamodelexamples">Beispiele für benutzerdefinierte Metamodelle.</a></p> </td> 
  </tr>
 </tbody> 
</table>

### Schlüsselwortbasierte Suche zum Anwenden von Eigenschaften auf Felder im generierten adaptiven Formular {#keywordsearch}

Der Dienst zur automatischen Formularkonvertierung führt während der Konvertierung eine Schlüsselwortsuche im Quellformular durch. Nach dem Filtern der Felder, die die Suchkriterien erfüllen, wendet der Konvertierungsdienst die für diese Felder im Metamodell definierten Eigenschaften auf die Felder im generierten adaptiven Formular an.

Auf Schlüsselwörter wird mit der Eigenschaft **aem:affKeyword** verwiesen.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

In diesem Beispiel verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach dem Abrufen des Textes **Bankkontonummer** im Formular konvertiert der Konvertierungsdienst das Feld mithilfe der Eigenschaft **type** in den Typ **number**.

### Zusätzliche Eigenschaften für Felder im generierten adaptiven Formular {#additionalproperties}

Mit der Eigenschaft **aem:afProperties** im Metamodell können Sie die folgenden zusätzlichen Eigenschaften für adaptive Formularfelder definieren, die mit dem Dienst für die automatische Formularkonvertierung generiert wurden:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Eigenschaftsname</strong></th> 
   <th><strong>Beschreibung</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiLine</p></td> 
   <td> 
    <p>Die Eigenschaft „multiLine“ konvertiert ein Quellformularfeld nach der Konvertierung in ein mehrzeiliges Feld im adaptiven Formular. Weitere Informationen finden Sie unter <strong>Konvertieren eines Zeichenfolgenfelds in ein mehrzeiliges Feld</strong> in <a href="#custommetamodelexamples">Beispiele für benutzerdefinierte Metamodelle.</a></p> </td> 
  </tr>
  <td><p>mandatory</p></td> 
   <td> 
    <p>Die Eigenschaft „mandatory“ legt die Eingabe für ein adaptives Formularfeld nach der Konvertierung als obligatorisch fest.<br>Weitere Informationen finden Sie unter <strong>Hinzufügen von Validierungen zu adaptiven Formularfeldern</strong> in <a href="#custommetamodelexamples">Metamodelle.</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>Mit der Eigenschaft „jcr:title“ mit der Eigenschaft JSON-Schemaeigenschaft „title“ können Sie die Bezeichnung eines adaptiven Formularfelds nach der Konvertierung ändern.<br>Weitere Informationen finden Sie unter <strong>Ändern der Beschriftung eines Formularfelds</strong> in <a href="#custommetamodelexamples">Beispiele für benutzerdefinierte Metamodelle.</a><br>Informationen zu weiteren Eigenschaften, die Sie mithilfe des JSON-Schemas auf adaptive Formularfelder anwenden können, finden Sie unter <a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">Erstellen adaptiver Formulare mit dem JSON-Schema</a>.</p>
    <p></p></td> 
  </tr>
  <td><p>sling: resourceType und guideNodeClass</p></td> 
   <td> 
    <p>Mit den Eigenschaften „sling:resourceType“ and „guideNodeClass“ können Sie ein Formularfeld einer entsprechenden adaptiven Formularkomponente zuordnen.<br>Weitere Informationen finden Sie unter <strong>Konvertieren eines Formularfelds in Multiple-Choice-Kontrollkästchen im adaptiven Formular</strong> und <strong>Konvertieren eines Textfelds in eine Dropdown-Liste im adaptiven Formular</strong> in <a href="#custommetamodelexamples">Beispiele für benutzerdefinierte Metamodelle.</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>Die Eigenschaft „validatePictureClause“ legt eine Überprüfung des Formats fest, das nach der Konvertierung für das Feld im adaptiven Formular zulässig ist.<br>Weitere Informationen finden Sie unter <strong>Hinzufügen von Validierungen zu adaptiven Formularfeldern</strong> in <a href="#custommetamodelexamples">Metamodelle.</p> </td> 
  </tr>
 </tbody> 
</table>

## Erstellen eines benutzerdefinierten Metamodells in Ihrer eigenen Sprache {#language-specific-meta-model}

Sie können ein sprachspezifisches Metamodell erstellen. Mit einem solchen Metamodell können Sie Zuordnungsregeln in der Sprache Ihrer Wahl erstellen. Mit dem Service für die automatische Formularkonvertierung können Sie Metamodelle in den folgenden Sprachen erstellen:

* Englisch (en)
* Französisch (fr)
* Deutsch (de)
* Spanisch (es)
* Italienisch (it)
* Portugiesisch (pt-br)

Fügen Sie das Metatag-Tag *aem:Language* oben in einem Metamodell hinzu, um die Sprache anzugeben. Beispiel:

```JSON
"metaTags": {
        "aem:Language": "fr"
    }
```

Wenn keine Sprache festgelegt ist, geht der Service davon aus, dass das Metamodell in englischer Sprache vorliegt.

### Überlegungen zum Erstellen eines sprachspezifischen Metamodells

* Stellen Sie sicher, dass der Name jedes Schlüssels englisch ist. Beispiel: e-mailAddress.
* Stellen Sie sicher, dass alle Entitätsverweise und vordefinierten Werte des ID-Schlüssels ausschließlich aus ASCII-Zeichen bestehen. Beispiel: &quot;id&quot;: &quot;ContactPoint&quot; / &quot;$ref&quot;: &quot;#ContactPoint&quot;.
* Stellen Sie sicher, dass alle Werte, die den folgenden Schlüsseln entsprechen, in der für das Metamodell festgelegten Sprache vorliegen.
   * aem:affKeyword
   * title
   * description
   * enumNames
   * shortDescription
   * validatePictureClauseMessage

   Wenn beispielsweise die Sprache des Metamodells Französisch ist (&quot;aem:Language&quot;: &quot;fr&quot;), stellen Sie sicher, dass alle Beschreibungen und Meldungen in französischer Sprache vorliegen.

* Stellen Sie sicher, dass alle [JSON-Schemaeigenschaften](#jsonschemaproperties) nur unterstützte Werte verwenden. Der Typ „property“ kann beispielsweise nur ausgewählte Werte der Kategorien „Zeichenfolge“, „Zahl“, „Ganzzahl“ und „Boolesch“ umfassen.

Die folgende Abbildung zeigt Beispiele für das englische Metamodell und das entsprechende französische Metamodell:

![](assets/language-specific-meta-model-comparison.png)

## Ändern von Feldern in adaptiven Formularen mit benutzerdefiniertem Metamodell {#modify-adaptive-form-fields-using-custom-meta-model}

Ihre Organisation kann Muster und Überprüfungen zusätzlich zu den im Standardmetamodell aufgeführten aufweisen. Sie können das Standardmetamodell erweitern, um Muster, Validierungen und Entitäten hinzuzufügen, die für Ihre Organisation spezifisch sind. Der Dienst für die automatische Formularkonvertierung wendet das benutzerdefinierte Metamodell während der Konvertierung auf die Formularfelder an. Sie können das Metamodell ständig aktualisieren, wenn neue Muster, Validierungen und Entitäten entdeckt werden, die für Ihre Organisation spezifisch sind.

Der Dienst für die automatische Formularkonvertierung verwendet ein Standardmetamodell, um während der Konvertierung die Felder des Quellformulars Feldern des adaptiven Formulars zuzuordnen. Das Standardmetamodell befindet sich unter dem folgenden Speicherort:

http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

Sie können jedoch ein benutzerdefiniertes Metamodell in einem Ordner speichern und die Eigenschaften des Konvertierungsdienstes ändern, sodass das benutzerdefinierte Metamodell während der Konvertierung verwendet wird.

### Verwenden eines benutzerdefinierten Metamodells während der Konvertierung {#use-custom-meta-model-during-conversion}

Führen Sie die folgenden Schritte aus, um während der Konvertierung ein benutzerdefiniertes Metamodell zu verwenden:

1. Erstellen Sie einen Ordner in **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]** und laden Sie die benutzerdefinierte JSON-Schemadatei für das Metamodell in den Ordner hoch.
1. Öffnen Sie die Eigenschaften des Konvertierungsdienstes mit:

   **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der automatischen Formularkonvertierung]** > **&lt;Eigenschaften der ausgewählten Konfiguration>**

1. Geben Sie auf der Registerkarte **[!UICONTROL Standard]** den Speicherort des benutzerdefinierten Metamodells im Feld **[!UICONTROL Benutzerdefiniertes Metamodell]** an und tippen Sie auf **[!UICONTROL Speichern und Schließen]**.
1. [Führen Sie die Konvertierung aus](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process), um das benutzerdefinierte Metamodell auf den Konvertierungsprozess anzuwenden.

### Benutzerdefinierte Metamodellbeispiele {#custommetamodelexamples}

Einige gängige Beispiele für die Verwendung eines benutzerdefinierten Metamodells zum Ändern der Eigenschaften von adaptiven Formularfeldern sind:

* Ändern der Beschriftung eines Formularfelds
* Ändern des Typs eines Formularfelds
* Hinzufügen von Hilfetext zu einem Formularfeld
* Konvertieren eines Formularfelds in Multiple-Choice-Optionsfelder im adaptiven Formular
* Ändern des Formats eines Formularfelds
* Hinzufügen von Validierungen zu adaptiven Formularfeldern
* Konvertieren eines Formularfelds in Dropdown-Listen-Optionen im adaptiven Formular
* Hinzufügen zusätzlicher Optionen zur Dropdown-Liste
* Konvertieren eines Zeichenfolgenfelds in ein mehrzeiliges Feld

#### Ändern der Beschriftung eines Formularfelds {#modify-the-label-of-a-form-field}

**Beispiel:** Ändern der Bezeichnung der Bankkontonummer im Formular in „Benutzerdefinierte Kontonummer“ im adaptiven Formular nach der Konvertierung.

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst die Eigenschaft **title** als Suchschlüsselwort. Nach dem Abrufen des Texts **Bankkontonummer** im Formular ersetzt der Konvertierungsdienst den Text durch die erwähnte Zeichenfolge **Benutzerdefinierte Kontonummer** mit der Eigenschaft **jcr:title** im Abschnitt **aem:afProperties**.

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

#### Ändern des Typs eines Formularfelds {#modify-the-type-of-a-form-field}

**Beispiel**: Ändern Sie das Feld **Bankkontonummer**, das vor der Konvertierung ein Textfeld im Formular ist, in ein Feld vom Typ „number“ im adaptiven Formular nach der Konvertierung.

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach dem Abrufen des Textes **Bankkontonummer** im Formular konvertiert der Konvertierungsdienst das Feld mithilfe der Eigenschaft **type** in den Typ „number“.

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

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach dem Abrufen des Textes **Bankkontonummer** im Formular fügt der Konvertierungsdienst den Hilfetext mithilfe der Eigenschaft **description** zum Feld des adaptiven Formulars hinzu.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "description": "Specify your bank account number."
 }
}
```

#### Konvertieren eines Formularfelds in Multiple-Choice-Kontrollkästchen im adaptiven Formular {#convert-a-form-field-to-multiple-choice-check-boxes-in-the-adaptive-form}

**Beispiel**: Konvertieren Sie das Feld **Land**, das vor der Konvertierung ein Zeichenfolgenfeld ist, in Kontrollkästchen im adaptiven Formular nach der Konvertierung.

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach Abrufen des Textes **Land** im Formular wandelt der Konvertierungsdienst das Feld mithilfe der Eigenschaft **Enum** in folgende Kontrollkästchen um:

* India
* England
* Australia
* New Zealand

Die Eigenschaften **sling:resourceType** und **guideNodeClass** ordnen ein Formularfeld der Kontrollkästchen-Komponente des adaptiven Formulars zu.

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

#### Ändern des Formats eines Formularfelds {#modify-the-format-of-a-form-field}

**Beispiel**: Ändern Sie das Format des Felds **E-Mail-Adresse** in ein E-Mail-Format.

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach Abrufen des Textes **E-Mail-Adresse** im Formular konvertiert der Konvertierungsdienst das Feld mithilfe der Eigenschaft **format** in das E-Mail-Format.

```
{
   "additionalDetails" : {
      "aem:affKeyword": ["E-mail Address"],
       "type" : "string",
       "format" : "email"
  } 
}
```

#### Hinzufügen von Validierungen zu adaptiven Formularfeldern {#add-validations-to-adaptive-form-fields}

**Beispiel 1:** Fügen Sie dem Feld **Postleitzahl** des adaptiven Formulars eine Validierung hinzu.

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach Abruf des Textes **Postleitzahl** im Formular fügt der Konvertierungsdienst dem Feld mithilfe der Eigenschaft **validatePictureClause**, definiert im Abschnitt **aem:afProperties**, eine Validierung hinzu. Gemäß dieser Validierung muss die Eingabe, die Sie nach der Konvertierung für das Feld **Postleitzahl** im adaptiven Formular angeben, sechs Zeichen lang sein.

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

**Beispiel 2:** Fügen Sie dem Feld **Bankkontonummer** des adaptiven Formulars eine Validierung hinzu.

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach Abruf des Textes **Bankkontonummer** im Formular fügt der Konvertierungsdienst dem Feld mithilfe der Eigenschaft **mandatory**, definiert im Abschnitt **aem:afProperties**, eine Validierung hinzu. Gemäß dieser Validierung müssen Sie nach der Konvertierung einen Wert für das Feld **Bankkontonummer** angeben, bevor Sie das Formular senden.

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

#### Konvertieren eines Testfelds in eine Dropdown-Liste im adaptiven Formular {#convert-a-text-field-to-drop-down-list-in-the-adaptive-form}

**Beispiel**: Konvertieren Sie das Feld **Land**, das vor der Konvertierung ein Zeichenfolgenfolgenfeld im Formular ist, in Dropdown-Optionen im adaptiven Formular nach der Konvertierung.

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach Abrufen des Textes **Land** im Formular wandelt der Konvertierungsdienst das Feld in die folgenden Dropdown-Listen-Optionen mit der Eigenschaft **enum** um:

* India
* England
* Australia
* New Zealand

Die Eigenschaften **sling:resourceType** und **guideNodeClass** ordnen ein Formularfeld der Dropdown-Komponente des adaptiven Formulars zu.

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

#### Hinzufügen zusätzlicher Optionen zur Dropdown-Liste {#add-additional-options-to-the-drop-down-list}

**Beispiel:** Fügen Sie **Sri Lanka** als zusätzliche Option zu einer vorhandenen Dropdown-Liste hinzu, indem Sie ein benutzerdefiniertes Metamodell verwenden.

Um eine zusätzliche Option hinzuzufügen, aktualisieren Sie die Eigenschaft **enum** mit der neuen Option. Aktualisieren Sie in diesem Beispiel die Eigenschaft **enum** mit **Sri Lanka** als zusätzliche Option. Die in der Eigenschaft **enum** aufgeführten Werte werden in der Dropdown-Liste angezeigt.

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

**Beispiel:** Konvertieren Sie das Feld **Adresse** vom Typ „string“ nach der Konvertierung in ein mehrzeiliges Feld im Formular.

In diesem benutzerdefinierten Metamodell verwendet der Konvertierungsdienst den Text in **aem:affKeyword** als Suchschlüsselwort. Nach dem Abrufen des Textes **Adresse** im Formular wandelt der Dienst das Textfeld mithilfe der Eigenschaft **multiLine**, die im Abschnitt **aem:afProperties** definiert ist, in ein mehrzeiliges Feld um.

```
{
 "multiLine" : {
   "aem:affKeyword": [
      "Address"
    ],
    "type" : "string",
    "aem:afProperties": {
      "multiLine": "true"
    }
  }
}
```
