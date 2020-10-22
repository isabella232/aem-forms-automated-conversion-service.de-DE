---
title: Bekannte Probleme
seo-title: Bekannte Probleme
description: bekannte Probleme und Einschränkungen für den Dienst für die automatische Formularkonvertierung
seo-description: Informieren Sie sich über die bekannten Probleme und Einschränkungen des Dienstes, bevor Sie den Dienst für die automatische Formularkonvertierung von AEM Forms verwenden
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
translation-type: tm+mt
source-git-commit: 589eacfd6200f4336b7a4a7708e10f3dfe08406d
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 95%

---

# Bekannte Probleme und Einschränkungen {#known-issues-limitations}

Überprüfen Sie die folgenden bekannten Probleme und Einschränkungen, bevor Sie mit der Verwendung des Dienstes für die automatische Formularkonvertierung von AEM Forms beginnen:

## Bekannte Probleme {#known-issues}

* Ordner mit zu konvertierenden Formularen sollten nicht mehr als 15 Formulare und insgesamt 50 Seiten enthalten. Die Größe des Quellordners sollte 10 MB nicht überschreiten. Erstellen Sie keine Unterordner im Quellordner.
* Einige Formularobjekte sind gut sichtbar für das menschliche Auge, sind aber [schwierig für den Dienst zu identifizieren](styles-and-pattern-considerations-and-best-practices.md). Verwenden Sie den [Editor „Überprüfen und Korrigieren“](review-correct-ui-edited.md), um solche Formularobjekte zu identifizieren und zu konvertieren.
* Editor „Überprüfen und Korrigieren“:

   * Hat keine Aktion „Rückgängig machen“. Die Schaltfläche „Speichern“ speichert die Änderungen dauerhaft.
   * Unterstützt keine wiederholbaren Bedienfelder für XFA-basierte Formulare.
   * Wenn Sie mit dem Editor „Überprüfen und korrigieren“ eine Liste in einer Tabelle ändern, wird die Zeilenbreite nicht automatisch angepasst und der Text erstreckt sich möglicherweise in die nächste Zeile der Tabelle.
   * Die Funktion **[!UICONTROL Mehrspaltiges Layout aus Eingabeformularen automatisch erkennen]** funktioniert nicht mit dem Editor „Überprüfen und Korrigieren“ und Formularfragmenten.
   * Scribble-Signatur, die mit Editor „Überprüfen und Korrigieren“ erstellt wurde, wird für veröffentlichte adaptive Formulare nicht geladen.


* Für XFA-basierte Formulare:
   * Das Extrahieren von Fragmenten aus einem XFA-basierten Formular wird nicht unterstützt.
   * XFA-Skripte werden nicht unterstützt. Zum Beispiel Skripte zum automatischen Generieren von Werten für eine Dropdown-Komponente.
   * Das Metamodell funktioniert nicht für die Auswahlgruppe
   * Option „Auswahlgruppen“ mit einem einzelnen Zeichen werden nicht identifiziert
   * Wenn das Quelldokument ein dynamisches XFA-Dokument (.XDP) ist und es [das Verhalten von XFA-Eigenschaften in einem adaptiven Formular definiert, ](https://helpx.adobe.com/de/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)wird die Präsenz-Eigenschaft des Quelldokuments nicht berücksichtigt. Wenn beispielsweise ein Feld im Quelldokument als ausgeblendet markiert ist und ein Skript das Feld sichtbar macht, bleibt das Feld im ausgegebenen adaptiven Formular sichtbar.

* Beachten Sie Folgendes, wenn Sie die Option **Eingabe AcroForm als Datensatzdokument (DoR) für generierte adaptive Formulare** verwenden:

<table>
    <tr>
        <td>Für zusammengesetzte Textfelder gehen Bindung und Daten verloren. In zusammengesetzten Textfeldern sind mehrere Textfelder aneinander ausgerichtet. In einem AcroForm wird beispielsweise eine Kreditkartennummer in mehrere Textfelder aufgeteilt, und jedes Textfeld verfügt über eine separate Bindung. Wenn das AcroForm in ein adaptives Formular konvertiert wird, hat das konvertierte adaptive Formular eine einzige Bindung für alle Textfelder. Um dieses Problem zu umgehen, ändern Sie vor dem Konvertieren eines AcroForm in ein adaptives Formular das AcroForm so, dass ein einzelnes Textfeld zum Akzeptieren von Kreditkartennummern verwendet wird.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>Für zusammengesetzte Datumsfelder gehen Bindung und Daten verloren. Ein zusammengesetztes Datumsfeld besteht aus drei verschiedenen Feldern. Beispielsweise wird ein Geburtsdatum in einem AcroForm in drei separate Felder aufgeteilt. Das adaptive Formular bietet eine sofort einsatzbereite Datumsauswahlkomponente. Um die Datumsauswahlkomponente des adaptiven Formulars zu verwenden und gleichzeitig die Bindung des AcroForm beizubehalten, müssen Sie das AcroForm vor der Konvertierung in ein adaptives Formular dahingehend ändern, dass es ein einzelnes Datumsfeld verwendet.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Wenn die Kontrollkästchen größer als der Begleittext sind, werden die Kontrollkästchen nicht erkannt und die Bindung im AcroForm geht verloren. Ändern Sie das AcroForm, wobei Sie die Kontrollkästchen kleiner als den Begleittext machen.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Wenn die Eingabefelder nicht am entsprechenden Textfeld ausgerichtet sind, wird das Eingabefeld nicht erkannt.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>Der Dienst konvertiert alle Kontrollkästchen eines AcroForm in separate Auswahlgruppen. Es werden separate Auswahlgruppen erstellt, um Bindungen in AcroForm beizubehalten. Führen Sie Auswahlgruppen im adaptiven Formular nicht zusammen. Dies führt zum Verlust von Bindungen. Wenn Sie die Auswahlgruppen zusammenführen, konvertieren Sie das Formular erneut, um die verlorenen Bindungen wiederherzustellen. </td>
        <td></td>
    </tr>
    <tr >
        <td>Die Grenzen einiger Tabellen werden in automatisch generierten Datensatzdokumenten (DoR) über den Seitenrand hinaus erweitert. </td>
        <td></td>
    </tr>
</table>

## Beschränkungen {#limitations}

* PDF-Formulare mit komplexem dynamischen Layout, Felder mit gepunktetem Umriss oder ausgefüllte Felder werden nicht unterstützt.
* Bilder und Text in den Bildern werden nicht identifiziert. Fügen Sie konvertierten Formularen manuell Bilder hinzu.
* Artwork XDP-Dokumente werden nicht unterstützt.
* PDF-Formulare mit mehr als 15 Seiten werden nicht unterstützt.
* Verschlüsselte, kennwortgeschützte und gesicherte Dokumente werden nicht konvertiert. Entfernen Sie die Verschlüsselung oder Kennwörter, bevor Sie die Konvertierung durchführen.
* Komplexe Tabellen wie randlose Tabellen, verschachtelte Tabellen und Tabellen mit Platzhalterwerten werden nicht unterstützt. Verwenden Sie den adaptiven Formulareditor, um nach der Konvertierung komplexe Tabellen hinzuzufügen oder zu ändern. Es werden nur einfache Tabellen mit leeren Feldern, richtigen Überschriften und klaren Grenzen unterstützt.
* Der Dienst konvertiert nur englischsprachige Formulare in adaptive Formulare. Sie können konvertierte adaptive Formulare mithilfe des [AEM Übersetzungs-Arbeitsablaufs](https://helpx.adobe.com/de/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html) in andere Sprachen übersetzen.
* AEM 6.4 Forms unterstützt keine automatische Erkennung des mehrspaltigen Layouts von Eingabeformularen.
* Informationen, die mit Farben im PDF-Quellformular kodiert wurden, werden nicht in das adaptive Formular übernommen.
* Die Farben des PDF-Quellformulars werden in Themen für adaptive Formulare übertragen.
* Farbige PDF forms werden wie Graustufenformulare behandelt und Felder werden entsprechend erkannt.

