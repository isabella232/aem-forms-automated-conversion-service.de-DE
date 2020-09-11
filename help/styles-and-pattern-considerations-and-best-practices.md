---
title: 'Best Practices und Hinweise '
seo-title: 'Best Practices und Hinweise '
description: Best Practices und Hinweise zum Dienst für die automatisierte Formularkonvertierung
seo-description: Liste der Stile und Muster in PDF-Quellformularen, die der Dienst für die automatische Formularkonvertierung nur schwer erkennen kann
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: e2298422e0af9b1c678e7604be3efb6da377d7dd
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 99%

---


# Best Practices und bekannte komplexe Muster {#Best-practices-and-considerations2}

Dieses Dokument enthält Richtlinien und Empfehlungen, von denen Formularadministratoren, Autoren und Entwickler profitieren können, wenn sie mit [!DNL Automated Forms Conversion service] arbeiten. Es werden bewährte Methoden erläutert, die von der Vorbereitung der Quellformulare bis zur Korrektur komplexer Muster reichen und für die automatisierte Konvertierung einen zusätzlichen Aufwand erfordern. Diese bewährten Methoden tragen zusammen zur Gesamtleistung und Ausgabe des [!DNL Automated Forms Conversion service] bei.

## Best Practices

Der Konvertierungsdienst konvertiert PDF-Formulare, die in Ihrer AEM [!DNL Forms]-Instanz verfügbar sind, in adaptive Formulare. Mit den unten aufgeführten Best Practices können Sie die Konvertierungsgeschwindigkeit und -genauigkeit verbessern. Darüber hinaus können Sie mit diesen Best Practices Zeit sparen, die Sie nach der Konvertierung aufgewendet haben.

### Vor dem Hochladen von Quellen

Sie können alle PDF-Formulare je nach Bedarf gleichzeitig oder schrittweise hochladen. Beachten Sie vor dem Hochladen der Formulare Folgendes:

* Ein Ordner muss weniger als 15 Formulare und weniger als 50 Seiten enthalten.
* Die Größe des Ordners muss kleiner als 10 MB sein. Speichern Sie Formulare nicht in einem Unterordner.
* Ein Formular muss weniger als 15 Seiten umfassen.
* Organisieren Sie Quelldokumente in einem Batch von 8-15 Dokumenten. Bewahren Sie Quellformulare mit gängigen adaptiven Formularfragmenten in einem einzigen Batch auf.
* Laden Sie die geschützten Formulare nicht hoch. Der Dienst konvertiert keine kennwortgeschützten und gesicherten Formulare.
* Laden Sie die [PDF-Portfolios](https://helpx.adobe.com/de/acrobat/using/overview-pdf-portfolios.html) nicht hoch. Der Dienst konvertiert keine PDF-Portfolios in ein adaptives Formular.
* Laden Sie keine gescannten, nicht englischsprachigen und ausgefüllten Formulare hoch. Solche Formulare werden nicht unterstützt.
* Laden Sie keine Quellformulare mit Leerzeichen im Dateinamen hoch. Entfernen Sie das Leerzeichen aus dem Namen der Datei, bevor Sie die Formulare hochladen.

Wenn Sie ein XDP-Formular für die Konvertierung verwenden, führen Sie die folgenden Schritte aus, bevor Sie die XPD-Quellformulare hochladen:

* Analysieren Sie das XDP-Formular und beheben Sie visuelle Probleme. Stellen Sie sicher, dass das Quelldokument die vorgesehenen Steuerelemente und Strukturen verwendet. Beispielsweise kann das Quellformular Kontrollkästchen anstelle von Optionsfeldern für eine einzelne Auswahl enthalten. Ändern Sie die Kontrollkästchen in Optionsfelder, um ein adaptives Formular mit den beabsichtigten Komponenten zu erstellen.
* [Fügen Sie dem XDP-Formular Bindungen hinzu](http://www.adobe.com/go/learn_aemforms_designer_65_de), bevor Sie mit der Konvertierung beginnen. Wenn Bindungen im XDP-Quellformular verfügbar sind, wendet der Dienst während der Konvertierung automatisch Bindungen auf entsprechende adaptive Formularfelder an. Sie sparen Zeit, die zum manuellen Anwenden der Bindungen erforderlich ist.
* [Fügen Sie der XDP-Datei Adobe Sign-Tags hinzu](https://helpx.adobe.com/sign/using/text-tag.html_de). Der Dienst konvertiert Adobe Sign-Tags automatisch in entsprechende adaptive Formularfelder. Adaptive Formulare unterstützen eine begrenzte Anzahl von Adobe Sign-Feldern. Die vollständige Liste der unterstützten Felder finden Sie in der Dokumentation [Verwenden von Adobe Sign in einem adaptiven Formular](https://docs.adobe.com/content/help/de/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html).
* Konvertieren Sie komplexe Tabellen in XDP-Dokumenten nach Möglichkeit in einfache Tabellen. Eine Tabelle mit Formularfeldern in Tabellenzellen, Zellen ungleicher Größe, zeilen- oder spaltenübergreifenden Zellen, zusammengeführten Zellen, Teilrändern oder keinem sichtbaren Rand wird als komplexe Tabelle betrachtet. Eine Tabelle mit einem der oben genannten Elemente wird als komplexe Tabelle betrachtet.
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### Vor dem Beginn der Konvertierung

* Adaptive Formularvorlagen erstellen Mithilfe von Vorlagen können Sie eine einheitliche Struktur für Formulare Ihrer Organisation oder Abteilung festlegen.
* Geben Sie die Kopf- und Fußzeile in den adaptiven Formularvorlagen an. Der Dienst ignoriert die Kopf- und Fußzeile von PDF-Quelldokumenten und verwendet die in der adaptiven Formularvorlage angegebene Kopfzeile.
* Themen für adaptive Formulare erstellen. Mithilfe von Themen können Formen Ihrer Organisation oder Abteilung einheitlich gestaltet werden.
* Konfigurieren Sie das Formulardatenmodell zum Speichern und Abrufen aus einer Datenquelle. Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Erstellen Sie adaptive Formularfragmente und konfigurieren Sie den Dienst für die Verwendung Ihrer adaptiven Formularfragmente.
* Bereiten Sie allgemeine Workflow-Modelle für die Formulare vor, die eine Automatisierung von Geschäftsprozessen erfordern.
* Konfigurieren Sie bei Bedarf Adobe Analytics


## Komplexe Muster kennen

AEM [!DNL Forms Automated Conversion service] verwendet künstliche Intelligenz und Algorithmen für maschinelles Lernen, um das Layout und die Felder des Quellformulars zu verstehen. Jeder auf maschinellem Lernen basierende Dienst lernt kontinuierlich aus den Quelldaten und liefert eine verbesserte Ausgabe. Diese Dienste lernen aus Erfahrung, genau wie Menschen.

[!DNL Automated Forms Conversion service] wird mit einer großen Formularmenge geschult. Er erkennt problemlos Felder in einem Quellformular und erzeugt adaptive Formulare. Es gibt jedoch einige Felder und Stile in PDF-Formularen, die für das menschliche Auge leicht sichtbar, für den Dienst jedoch schwer zu verstehen sind. Der Dienst weist einigen Feldern oder Stilen eventuell andere als die zutreffenden Feldtypen oder Bedienfelder zu. Alle diese Feld- und Stilmuster sind nachfolgend aufgeführt.

Der Dienst beginnt, diese Muster zu erkennen und ihnen die richtigen Felder oder Bedienfelder zuzuweisen, da er weiterhin aus den Quelldaten lernt. Derzeit können Sie den Editor [Überprüfen und Korrigieren](review-correct-ui-edited.md) verwenden, um solche Probleme zu beheben. Machen Sie sich mit [adaptiven Formularkomponenten](https://helpx.adobe.com/de/experience-manager/6-5/forms/using/introduction-forms-authoring.html) vertraut, bevor Sie mit der Behebung der Probleme beginnen oder weiterlesen.

### Allgemeine Muster {#general}

| Muster | Beispiel |
|--- |--- |
| **Muster** <br>Der Dienst konvertiert keine ausgefüllten PDF-Formulare in adaptive Formulare. <br><br>**Lösung** <br>Verwenden Sie leere adaptive Formulare. | ![Ausgefülltes Formular](assets/best-practice-filled-forms.png) |
| **Muster** <br>Der Dienst kann Text und Felder möglicherweise nicht erkennen, wenn sie im Formular zu dicht beieinander stehen. <br><br>**Lösung** <br> Erhöhen Sie die Breite zwischen Text und Feldern eines dichten Formulars, bevor Sie mit der Konvertierung beginnen. |  |
| **Muster** <br>Der Dienst unterstützt keine gescannten Formulare. <br><br>**Lösung** <br>Verwenden Sie keine gescannten Formulare. | ![Gescanntes Formular](assets/scanned-forms.png) |
| **Muster** <br>Der Dienst extrahiert keine Bilder und Texte in Bildern. <br><br>**Lösung**<br> Fügen Sie den konvertierten Formularen manuell Bilder oder Text hinzu. | ![Bild mit Textformular](assets/best-practice-image-with-text.png) |
| **Muster** <br>Tabellen mit gepunkteten oder unklaren Begrenzungen und Rahmen werden nicht konvertiert. <br><br>**Lösung** <br>Verwenden Sie Tabellen mit klaren expliziten Grenzen und Rahmen. unterstützt. | ![Nicht eindeutiges Tabellenformular](assets/best-practice-table-dotted-non-clear.png) |
| **Muster** <br> Das adaptive Formular unterstützt keinen sofort einsatzbereiten vertikalen Text. Der Dienst konvertiert daher keinen vertikalen Text in den entsprechenden Text für adaptive Formulare. <br><br>**Lösung** <br> Verwenden Sie bei Bedarf den adaptiven Formulareditor, um vertikalen Text hinzuzufügen. | ![Nicht eindeutiges Tabellenformular](assets/vertical-text.png) |



### Auswahlgruppe  {#choice-group}

| Muster | Lösung |
|--- |--- |
| **Muster** <br> Auswahlgruppen mit anderen Formen als „Kästchen“ oder „Kreis“ werden nicht in entsprechende adaptive Formularkomponenten konvertiert. <br><br>**Lösung** <br>Ändern Sie die Formen der Auswahloptionen in ein Kästchen oder einen Kreis, oder verwenden Sie den Editor „Überprüfen und Korrigieren“, um die Formen zu identifizieren. | ![Auswahlfelder ](assets/best-practice-choice-group-options.png) |

### Formularfelder {#form-fields}

| Muster | Lösung |
|--- |--- |
| **Muster** <br>Der Dienst erkennt keine Felder ohne klare Rahmen. <br><br>**Lösung** <br>Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Felder zu identifizieren. | ![Felder mit unklaren Begrenzungen](assets/best-practice-fields-without-clear-borders.png) |
| **Muster** <br> Der Dienst erkennt möglicherweise keine Auswahlgruppenformularfelder mit Beschriftungen am unteren oder rechten Rand eines Formulars. <br><br>**Lösung** <br>Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Felder zu identifizieren. | ![Auswahlfelder](assets/best-practice-caption-bottom-right.png) |
| **Muster** <br> Der Dienst führt einige Formularfelder zusammen oder weist ihnen einen falschen Typ zu, wenn sie sehr nahe beieinander liegen oder keine klaren Grenzen haben. <br><br>**Lösung** <br>Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Felder zu identifizieren. | ![Auswahlfelder](assets/best-practice-placed-very-near.png) |
| **Muster** <br>Der Dienst kann Felder mit weit entfernten Beschriftungen oder einer gepunkteten Linie zwischen Beschriftung und Eingabefeld möglicherweise nicht erkennen. <br><br>**Lösung** <br>Verwenden Sie Formularfelder mit klaren Begrenzungen oder den Editor „Überprüfen und Korrigieren“, um diese Probleme zu beheben. | ![Weit entfernte Felder oder gepunktete Linie zwischen dem Beschriftungsfeld](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Listen {#lists}

| Muster | Lösung |
|--- |--- |
| **Muster** <br>Listen, die Formularfelder enthalten, werden zusammengeführt oder nicht in entsprechende adaptive Formularkomponenten konvertiert. <br><br>**Lösung** <br>Verwenden Sie Formularfelder mit klaren Grenzen oder den Editor „Überprüfen und Korrigieren“, um solche Probleme zu beheben. | ![Listen mit Auswahlgruppen](assets/best-practice-lists-containing-form-fields.png) |
| **Muster** <br>Der Dienst kann einige verschachtelte Listen nicht identifizieren.<br><br>**Lösung** <br> Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Probleme zu beheben. | ![Listen mit Auswahlgruppen](assets/best-practice-nested-lists.png) |
| **Muster** <br>Der Dienst führt einige Listen mit Auswahlgruppen zusammen.<br><br>**Lösung** <br> Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Probleme zu beheben. | ![Listen mit Auswahlgruppen](assets/best-practice-check-box-in-table-cells.png) |

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fields without borders are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->
