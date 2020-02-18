---
title: Bekannte Probleme
seo-title: Bekannte Probleme
description: Bekannte Probleme und Einschränkungen beim Konvertierungsdienst für automatisierte Formulare
seo-description: Bevor Sie mit der Verwendung des AEM Forms Automated Forms Conversion-Dienstes beginnen, sollten Sie sich mit den bekannten Problemen und Einschränkungen des Dienstes vertraut machen
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
translation-type: tm+mt
source-git-commit: 2fcceb45d9be4297fcd923f5a17c7b593294e855

---

# Known issues and limitations {#known-issues-limitations}

Bevor Sie mit der Verwendung des AEM Forms Automated Forms Conversion-Dienstes beginnen, überprüfen Sie die folgenden bekannten Probleme und Einschränkungen:

## Bekannte Probleme {#known-issues}

* Ordner, die Formulare zur Konvertierung enthalten, sollten nicht mehr als 15 Formulare und 50 Seiten umfassen. Die Größe des Quellordners darf 10 MB nicht überschreiten. Erstellen Sie keine Unterordner im Quellordner.
* Einige Formularobjekte sind für das menschliche Auge leicht sichtbar, für den Dienst jedoch [schwer zu identifizieren](styles-and-pattern-considerations-and-best-practices.md). Verwenden Sie den [Überprüfungs- und den richtigen Editor](review-correct-ui-edited.md) , um solche Formularobjekte zu identifizieren und zu konvertieren.
* Überprüfungs- und Korrektur-Editor:

   * Hat keine Rückgängig-Aktion. Über die Schaltfläche Speichern werden die Änderungen dauerhaft gespeichert.
   * Unterstützt keine wiederholbaren Bereiche für XFA-basierte Formulare.
   * Wenn Sie eine Liste in einer Tabelle mit dem Editor &quot;Überprüfen&quot;und &quot;Korrigieren&quot;ändern, wird die Zeilenbreite nicht automatisch angepasst und der Text wird möglicherweise zur nächsten Zeile der Tabelle verschoben.
   * Die **[!UICONTROL Auto-detect multi-column layout from input forms]** Funktion funktioniert nicht mit den Editoren zum Überprüfen und Korrigieren und Formularfragmenten.

* Für XFA-basierte Formulare:
   * Das Extrahieren von Fragmenten aus einem XFA-basierten Formular wird nicht unterstützt.
   * XFA-Skripten werden nicht unterstützt. Beispielsweise Skripten zur automatischen Generierung von Werten für eine Dropdown-Komponente.
   * Meta-Modell funktioniert nicht für die Auswahlgruppe
   * Die Option &quot;Auswahlgruppen&quot;mit einem einzelnen Zeichen wird nicht identifiziert
   * Wenn das Quelldokument eine dynamische XFA (.XDP) ist und das Verhalten von XFA-Eigenschaften in einem adaptiven Formular[](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)definiert, wird die presence-Eigenschaft des Quelldokuments nicht berücksichtigt. Beispielsweise wird ein Feld im Quelldokument als ausgeblendet markiert und ein Skript macht das Feld sichtbar, dann bleibt das Feld im adaptiven Formular für die Ausgabe sichtbar.

* Wenn Sie die Option &quot;AcroForm als Datensatzdokument **verwenden (DoR)&quot;für erstellte adaptive Formulare** verwenden, beachten Sie Folgendes:

<table>
    <tr>
        <td>Bindung und Daten gehen für zusammengesetzte Textfelder verloren. Bei zusammengesetzten Textfeldern sind mehrere Textfelder aufeinander abgestimmt. In einem AcroForm wird beispielsweise eine Kreditkartennummer in mehrere Textfelder aufgeteilt und jedes Textfeld hat eine separate Bindung. Wenn das AcroForm in ein adaptives Formular konvertiert wird, enthält das konvertierte adaptive Formular eine Bindung für alle Textfelder. Um dies zu umgehen, ändern Sie vor der Konvertierung eines AcroForm in ein adaptives Formular das AcroForm-Formular, um ein einzelnes Textfeld zu verwenden, damit Kreditkartennummern akzeptiert werden.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>Bindung und Daten gehen für zusammengesetzte Datumsfelder verloren. Ein zusammengesetztes Datumsfeld besteht aus drei verschiedenen Feldern. Beispielsweise wird ein Geburtsfeld in einem AcroForm in drei separate Felder unterteilt. Das adaptive Formular bietet eine voreingestellte Komponente zur Datumsauswahl. Um die Datumsauswahl-Komponente des adaptiven Formulars zu verwenden und dabei die Bindung des AcroForm beizubehalten, ändern Sie vor der Konvertierung eines AcroForm in ein adaptives Formular das AcroForm-Feld, um ein einzelnes Datumsfeld zu verwenden.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Wenn die Größe der Kontrollkästchen größer als der zugehörige Text ist, werden die Kontrollkästchen nicht erkannt und die Bindung im AcroForm geht verloren. Ändern Sie das AcroForm, um die Größe der Kontrollkästchen kleiner als der zugehörige Text zu machen.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Wenn die Eingabefelder nicht mit dem entsprechenden Textfeld übereinstimmen, wird das Eingabefeld nicht erkannt.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>Der Dienst konvertiert alle Kontrollkästchen eines AcroForm in separate Auswahlgruppen. Separate Auswahlgruppen werden erstellt, um Bindungen mit AcroForm beizubehalten. Führen Sie keine Auswahlgruppen im adaptiven Formular zusammen. Es wird zu einem Verlust von Bindungen führen. Wenn Sie die Auswahlgruppen zusammenführen, konvertieren Sie das Formular erneut, um die verlorenen Bindungen wiederherzustellen. </td>
        <td></td>
    </tr>
    <tr >
        <td>Die Begrenzungen einiger Tabellen werden im automatisch generierten Datensatzdokument (DoR) von der Seite entfernt. </td>
        <td></td>
    </tr>
</table>

## Beschränkungen {#limitations}

* PDF-Formulare mit komplexem dynamischem Layout, Felder mit gepunkteter Kontur, ausgefüllten Feldern oder farbigen Feldern werden nicht unterstützt.
* Bilder und Text innerhalb der Bilder werden nicht identifiziert. Fügen Sie den konvertierten Formularen manuell Bilder hinzu.
* Grafik-XDP-Dokumente werden nicht unterstützt.
* PDF-Formulare mit mehr als 15 Seiten werden nicht unterstützt.
* Verschlüsselte, kennwortgeschützte und geschützte Dokumente werden nicht konvertiert. Entfernen Sie Verschlüsselung oder Kennwörter, bevor Sie die Konvertierung ausführen.
* Komplexe Tabellen wie randlose Tabellen, verschachtelte Tabellen, Tabellen mit farbigen Zeilen und Tabellen mit Platzhalterwerten werden nicht unterstützt. Verwenden Sie den Editor für adaptive Formulare, um nach der Konvertierung komplexe Tabellen hinzuzufügen oder zu ändern. Es werden nur einfache Tabellen mit leeren Feldern, richtigen Kopfzeilen und klaren Begrenzungen unterstützt.
* Der Dienst konvertiert nur englischsprachige Formulare in adaptive Formulare. Sie können konvertierte adaptive Formulare mit dem [AEM-Übersetzungs-Workflow](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)in eine andere Sprache übersetzen.
* AEM 6.4 Forms unterstützt nicht die automatische Erkennung von mehrspaltigen Layouts von Eingabeformularen.

