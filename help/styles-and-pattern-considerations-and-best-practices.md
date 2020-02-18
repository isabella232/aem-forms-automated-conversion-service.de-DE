---
title: 'Bewährte Verfahren und Überlegungen '
seo-title: 'Bewährte Verfahren und Überlegungen '
description: Bewährte Verfahren und Überlegungen zum Dienst für die automatisierte Formularkonvertierung
seo-description: Liste von Stilen und Mustern in PDF-Quellformularen, die vom Dienst für die automatisierte Formularkonvertierung schwer zu identifizieren ist
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: 0f413a8bc0bb444b6faaddaf32f84f36e38438a5

---


# Bewährte Verfahren und bekannte komplexe Muster {#Best-practices-and-considerations2}

Dieses Dokument enthält Richtlinien und Empfehlungen, von denen Forms-Administratoren, -Autoren und -Entwickler profitieren können, wenn sie mit dem Automatisierten Forms-Konvertierungsdienst arbeiten. Es beschreibt bewährte Verfahren, angefangen bei der Vorbereitung von Quellformularen bis zur Behebung komplexer Muster, die zusätzliche Anstrengungen zur automatischen Konvertierung erfordern. Diese Best Practices tragen zusammen zur Gesamtleistung und Ausgabe des automatisierten Formularkonvertierungsdiensts bei.

## Best Practices

Der Konvertierungsdienst konvertiert PDF-Formulare, die in Ihrer AEM Forms-Instanz verfügbar sind, in adaptive Formulare. Sie können bei Bedarf alle PDF-Formulare gleichzeitig oder in einem bestimmten Zeitabschnitt hochladen. Beachten Sie vor dem Hochladen der Formulare Folgendes:

* Halten Sie die Anzahl der Formulare in einem Ordner unter 15 und behalten Sie die Gesamtanzahl der Seiten in einem Ordner unter 50.
* Halten Sie die Größe des Ordners unter 10 MB. Speichern Sie keine Formulare in einem Unterordner.
* Halten Sie die Anzahl der Seiten in einem Formular unter 15.
* Laden Sie die geschützten Formulare nicht hoch. Der Dienst konvertiert keine kennwortgeschützten und geschützten Formulare.
* Laden Sie die [PDF-Portfolios](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)nicht hoch. Der Dienst konvertiert kein PDF-Portfolio in adaptive Formulare.
* Laden Sie keine gescannten, farbigen, nicht englischsprachigen und ausgefüllten Formulare hoch. Solche Formulare werden nicht unterstützt.
* Laden Sie keine Quellformulare mit Leerzeichen im Dateinamen hoch. Entfernen Sie den Leerraum aus dem Namen der Datei, bevor Sie die Formulare hochladen.
* Verwenden Sie Vorlagen für adaptive Formulare, um Kopf- und Fußzeile für das adaptive Formular für die Ausgabe anzugeben. Der Dienst ignoriert die Kopf- und Fußzeile von PDF-Quelldokumenten und verwendet die in der Vorlage für adaptive Formulare angegebene Kopfzeile.

## Komplexe Muster kennen

Der AEM Forms Automated Conversion-Dienst verwendet Algorithmen für künstliche Intelligenz und maschinelles Lernen, um das Layout und die Felder des Quellformulars zu verstehen. Jeder maschinelle Lerndienst lernt ständig aus den Quelldaten und erzeugt mit jeder Kehrtwende eine verbesserte Ausgabe. Diese Dienste lernen von Erfahrungen wie Menschen.

Der Dienst für die automatisierte Formularkonvertierung wird für eine große Anzahl von Formularen geschult. Es identifiziert einfach Felder in einem Quellformular und erzeugt adaptive Formulare. Es gibt jedoch einige Felder und Stile in PDF-Formularen, die für das menschliche Auge leicht sichtbar, aber für den Dienst schwer zu verstehen sind. Der Dienst kann bestimmten Feldern oder Stilen unterschiedliche Feldtypen oder Bereiche zuweisen. Alle diese Felder- und Stilmuster sind unten aufgeführt.

Der Dienst würde beginnen, diese Muster zu identifizieren und ihnen korrekte Felder oder Bereiche zuzuweisen, da er weiterhin aus den Quelldaten lernt. Vorläufig können Sie diese Probleme mit dem Editor &quot; [Überprüfen&quot;und &quot;Korrigieren](review-correct-ui-edited.md) &quot;beheben. Bevor Sie mit der Behebung der Probleme beginnen oder weitere Informationen lesen, sollten Sie sich mit den [adaptiven Formularkomponenten](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)vertraut machen.

### Allgemeine Muster {#general}

| Muster | Auflösung |
|--- |--- |
| **Der Musterdienst** konvertiert keine farbigen PDF-Formulare <br> in adaptive Formulare. <br><br>**Auflösung **<br>Verwenden Sie PDF-Formulare in Schwarzweiß oder Graustufen. | ![Farbiges Formular](assets/best-practice-coloured-forms.png) |
| **Der Musterdienst** konvertiert <br>keine ausgefüllten PDF-Formulare in adaptive Formulare. <br><br>**Auflösung **<br>Verwenden Sie leere adaptive Formulare. | ![Ausgefülltes Formular](assets/best-practice-filled-forms.png) |
| **Der Musterdienst** kann <br>Text und Felder in einem dichten Formular nicht erkennen. <br><br>**Auflösung **<br>Erhöhen Sie die Breite zwischen Text und Feldern eines dichten Formulars, bevor Sie mit der Konvertierung beginnen. |  |
| **Der Musterdienst** <br>unterstützt keine gescannten Formulare. <br><br>**Auflösung **<br>Verwenden Sie keine gescannten Formulare. | ![Gescanntes Formular](assets/scanned-forms.png) |
| **Der Musterdienst** extrahiert <br>keine Bilder und keinen Text in Bildern. <br><br>**Auflösung **<br>Fügen Sie den konvertierten Formularen manuell Bilder oder Text hinzu. | ![Bild mit Textformular](assets/best-practice-image-with-text.png) |
| **Mustertabellen** mit gepunkteten oder unklaren <br>Begrenzungen und Rahmen werden nicht konvertiert. <br><br>**Auflösung **<br>Verwenden Sie Tabellen mit klaren und eindeutigen Begrenzungen. unterstützt. | ![Nicht eindeutiges Tabellenformular](assets/best-practice-table-dotted-non-clear.png) |
| **Muster** <br> Adaptives Formular unterstützt nicht standardmäßig vertikalen Text. Der Dienst konvertiert daher keinen vertikalen Text in den entsprechenden Text für adaptive Formulare. <br><br>**Auflösung **<br>Verwenden Sie den Editor für adaptive Formulare, um bei Bedarf vertikalen Text hinzuzufügen. | ![Nicht eindeutiges Tabellenformular](assets/vertical-text.png) |



### Auswahlgruppe {#choice-group}

| Muster | Auflösung |
|--- |--- |
| **Optionen für Muster** - <br> Auswahlgruppen mit anderen Formen als &quot;Feld&quot;oder &quot;Kreis&quot;werden nicht in entsprechende adaptive Formularkomponenten konvertiert. <br><br>**Auflösung **<br>Ändern Sie Auswahloptionen in Form von Feldern oder Kreisen oder verwenden Sie den Editor Überprüfen und Korrigieren, um die Formen zu identifizieren. | ![Auswahlfelder ](assets/best-practice-choice-group-options.png) |

### Form fields {#form-fields}

| Muster | Auflösung |
|--- |--- |
| **Der Musterdienst** identifiziert keine Felder ohne klare Grenzen <br> . <br><br>**Lösung **<br>Verwenden Sie den Editor &quot;Review&quot;und &quot;Richtig&quot;, um solche Felder zu identifizieren. | ![Felder mit nicht klaren Grenzen](assets/best-practice-fields-without-clear-borders.png) |
| **Der Musterdienst** <br> identifiziert möglicherweise keine Auswahlgruppenformularfelder mit Beschriftungen am unteren oder rechten Rand eines Formulars. <br><br>**Auflösung **<br>Verwenden Sie den Editor &quot;Überprüfung&quot;und &quot;Richtig&quot;, um solche Felder zu identifizieren | ![Auswahlfelder](assets/best-practice-caption-bottom-right.png) |
| **Der Musterdienst** <br> führt einige Formularfelder zusammen oder weist ihnen einen falschen Typ zu, die sehr nahe beieinander liegen oder keine klaren Ränder aufweisen. <br><br>**Lösung **<br>Verwenden Sie den Editor &quot;Review&quot;und &quot;Richtig&quot;, um solche Felder zu identifizieren. | ![Auswahlfelder](assets/best-practice-placed-very-near.png) |
| **Der Musterdienst** kann Felder mit weit entfernten Beschriftungen oder einer gepunkteten Linie zwischen dem Beschriftungs- und dem Eingabefeld nicht erkennen <br> . <br><br>**Lösung **<br>Verwenden Sie Formularfelder mit klaren Begrenzungen oder verwenden Sie den Editor zum Überprüfen und Korrigieren, um diese Probleme zu beheben. | ![Entfernt Felder oder gepunktete Linie zwischen Beschriftungsfeldern](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Listen {#lists}

| Muster | Auflösung |
|--- |--- |
| **Musterlisten** , die <br>Formularfelder enthalten, werden zusammengeführt oder nicht in entsprechende adaptive Formularkomponenten konvertiert. <br><br>**Lösung **: Formularfelder mit klaren Grenzen<br>verwenden oder den Editor zum Überprüfen und Korrigieren verwenden, um solche Probleme zu beheben. | ![Listen mit Auswahlgruppen](assets/best-practice-lists-containing-form-fields.png) |
| **Der Musterdienst** <br>kann einige verschachtelte Listen als nicht identifizierte <br><br>**Auflösungsdatei **<br>mit dem Editor Überprüfung und Korrektur verwenden lassen, um solche Probleme zu beheben. | ![Listen mit Auswahlgruppen](assets/best-practice-nested-lists.png) |
| **Der Musterdienst** führt einige Listen mit Auswahlgruppen zusammen, um diese Probleme zu beheben, indem er die <br>Auflösungs<br><br>** - **<br>und Überprüfungs-Editor verwendet. | ![Listen mit Auswahlgruppen](assets/best-practice-check-box-in-table-cells.png) |

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
