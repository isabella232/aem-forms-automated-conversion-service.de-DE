---
title: Überprüfen und Korrigieren konvertierter Formulare
seo-title: Überprüfen und Korrigieren konvertierter Formulare
description: Überprüfen und korrigieren Sie die adaptiven Formulare, die vom Konvertierungsdienst für automatisierte Formulare konvertiert wurden.
seo-description: Überprüfen und Korrigieren der adaptiven Formulare, die vom Konvertierungsdienst für automatisierte Formulare konvertiert wurden
uuid: 5a0a6d24-dff6-4732-b607-24848b07b26d
topic-tags: forms
discoiquuid: f45ab2d7-5234-42d6-aeb6-b2cb1a7ce3c2
translation-type: tm+mt
source-git-commit: 3303c72b7d644dd183c036ba3cc48e629a9a503e

---


# Überprüfen und Korrigieren konvertierter Formulare{#review-and-correct-converted-forms}

Der AEM Forms Automated Forms Conversion-Dienst identifiziert Felder, Inhalte und das Layout des PDF-Eingabedokuments und konvertiert das PDF-Dokument in ein adaptives Formular. Das adaptive Formular für die Ausgabe kann einige fehlende oder falsch konvertierte Felder enthalten. Sie können den Editor &quot;Überprüfen&quot;und &quot;Korrigieren&quot;verwenden, um die identifizierten Felder zu verbessern und das adaptive Formular neu zu generieren, um eine Ausgabe näher an das gewünschte Erlebnis heranzubringen. Nach der ersten Konvertierung können Sie das PDF-Eingabedokument im Editor öffnen, um:

* Alle Felder und Inhalte anzeigen, die während der Konvertierung identifiziert wurden
* Identifizieren Sie die Felder und Inhalte, die während der Konvertierung ausgelassen wurden.
* Überprüfen Sie den Feldtyp und ändern Sie ihn bei Bedarf
* Überprüfen der identifizierten Tabellen, Ändern der Spaltengröße und Ändern des Zelleninhalts
* Zu Unrecht identifizierte Felder entfernen

Nachdem Sie die erforderlichen Änderungen vorgenommen haben, senden Sie die PDF-Formulare an den Konvertierungsdienst. Bei erfolgreicher Konvertierung werden aktualisierte Assets, einschließlich des adaptiven Formulars und Schemas, in Ihre AEM Forms-Instanz heruntergeladen. Sie können den Prozess wiederholen, bis das gewünschte Erlebnis erreicht ist. ![](assets/stages-of-form-2.gif)

Sie benötigen Google Chrome, Mozilla FireFox oder den Microsoft Edge-Browser, um den Review- und den korrekten Editor zu verwenden. Internet Explorer wird vom Editor nicht unterstützt.

## Willkommen beim Editor für Review und Korrektur {#welcome-to-review-and-correct-editor}

Der Editor &quot;Überprüfen und korrigieren&quot;bietet eine benutzerfreundliche Oberfläche. Es enthält die folgenden Komponenten:

* Content Browser: Sie können den Inhaltsbrowser verwenden, um die Position eines Elements zu ändern. Mit dem Inhaltsbrowser können Sie ein Formularobjekt per Drag &amp; Drop verschieben, um seine Position zu ändern. Verschieben einer Tabelle beispielsweise vor einem Textfeld Die Tab-Reihenfolge des adaptiven Formulars für die Ausgabe wird entsprechend geändert.
* Eigenschaftenbrowser: Es zeigt die Eigenschaften eines ausgewählten Felds an. Sie können auch die Eigenschaften ändern.
* Symbolleiste: Die Symbolleiste befindet sich oben im Editor. Es werden Werkzeuge zum Hinzufügen, Ändern, Gruppieren, Aufheben und Löschen von Feldern angezeigt.
* Eigenschaften öffnen: Die Option &quot;Eigenschaften öffnen&quot;wird angezeigt, wenn Sie auf das ![](assets/properties.png) Symbol tippen. Sie können auf Eigenschaften öffnen klicken, um die Formulareigenschaften zu öffnen und weitere Optionen anzuzeigen.
* Filterschaltfläche: Die Filterschaltfläche ![](assets/toggle_eye.png) befindet sich oben im Editor. Sie können die Felder so filtern, dass nur Texte, Felder, Auswahlgruppen, Bereiche oder alle Komponenten angezeigt werden.
* Schaltfläche &quot;Speichern&quot;: Die **[!UICONTROL Save]** Schaltfläche befindet sich in der oberen rechten Ecke des Editors. Sie können auch mit dem Pfeil neben der Schaltfläche Speichern die Option zum Senden des Formulars zur Konvertierung anzeigen.

* PDF-Formular: Der Editor zeigt das PDF-Quelldokument an und überlagert es mit identifizierten Feldern. Sie können die Felder mit den Werkzeugen der Symbolleiste ändern.
* Seiten: Ein Quellformular kann mehrere Seiten haben. Der Editor bietet eine Schaltfläche in der rechten oberen Ecke, um zwischen den Seiten zu navigieren.

![Benutzeroberfläche überprüfen und korrigieren](assets/reviewcorrectui.png)

**************A. Inhaltsbrowser** B. Eigenschaftenbrowser **C.** Symbolleiste **D. Schaltfläche &quot;Eigenschaften&quot;** E. Filterschaltfläche **F. Schaltfläche** G speichern. PDF-Formular mit identifizierten Feldern überlagert

Nach der ersten erfolgreichen Konvertierung überlagert der Konvertierungsdienst das PDF-Quelldokument mit identifizierten Feldern und Komponenten. Diese Felder oder Komponenten sind vom Typ: Text, Feld, Bereich, Auswahlgruppe und Tabelle:

* Text: Text im PDF-Quelldokument. Beispiel: Der Text für die Kreditanwendung in der Abbildung oben.
* Feld: Kombination von Text oder Symbolbeschriftung, die mit einem Wert oder Eingabefeld verknüpft ist. Beispiel: Der Vorfeldname in der Abbildung oben. Es verfügt über eine Textbeschriftung und ein Eingabefeld. Ein Feld unterstützt die Datentypen Text, Nummerisch, Dropdown, Datum, E-Mail, Telefonnummer, Unterschrift, Währung und Kennwort.
* Bereich: Logische Sammlung von Inhalten und Komponenten. Beispiel: Persönliche Details der Bedienfelder &quot;Person 1&quot;und &quot;Person 2&quot;in oben stehender Abbildung.
* Auswahlgruppe: Kombination von Text, der mit mehreren Auswahloptionen verknüpft ist: Kontrollkästchen und Optionsfeld. Zum Beispiel Familienstand und vorhandener Kunde in oben stehender Abbildung.\
   Je nach Auswahlgruppenbeschriftung und den Optionen für mehrere Auswahlen konvertiert der Konvertierungsdienst automatisch eine Auswahlgruppe in ein Optionsfeld oder ein Kontrollkästchen mit mehreren Auswahlen. Wenn zum Beispiel eine Auswahl **auswählen** ist, da die Auswahlgruppenkoption oder die Mehrfachauswahl-Optionen es Ihnen ermöglichen, nur eine Option auszuwählen: **Ja** oder **Nein**, konvertiert der Konvertierungsdienst die Auswahlgruppe automatisch in ein Optionsfeld mit nur einer Auswahl. Gleichermaßen wandelt der Konvertierungsdienst die Auswahlgruppe automatisch in ein Kontrollkästchen mit mehreren Auswahlen um, wenn alle Auswahlgruppen **auswählen, die mehrere Optionen anwenden** oder mehrere **Optionen** auswählen, als Auswahlgruppenbeschriftung oder mit den Mehrfachoptionen.

* Tabelle: Eine 2-D-Tabelle mit Informationen, die in Spalten und Zeilen dargestellt werden. Sie können einer Tabelle Zeilen oder Spalten hinzufügen oder entfernen.

## Konvertierung überprüfen {#start-reviewing-a-conversion}

Nach der ersten erfolgreichen Konvertierung überlagert der Konvertierungsdienst das PDF-Quelldokument mit identifizierten Feldern und Komponenten. Sie können Verbesserungen an identifizierten Feldern vornehmen und das adaptive Formular neu generieren, um eine Ausgabe näher an das gewünschte Erlebnis heranzuführen. Sie können eine Konvertierung erst nach der ersten erfolgreichen Konvertierung überprüfen.

### Bevor Sie beginnen {#before-you-start}

* Der Editor &quot;Überprüfen&quot;und &quot;Korrigieren&quot;unterstützen keine Fragmente. Verwenden Sie den Editor nicht, um Konvertierungen zu überprüfen, bei denen die Option &quot;Fragment **extrahieren** &quot;während der Konvertierungen aktiviert war. Sie können für solche Konvertierungen den [Editor](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html) für adaptive Formulare verwenden.

* Im Editor &quot;Überprüfen&quot;und &quot;Korrigieren&quot;wird die Aktion &quot;Rückgängig&quot;nicht ausgeführt. Verwenden Sie die Schaltfläche Speichern nur, um die Änderungen dauerhaft zu speichern.

### Review starten {#start-the-review}

Um Konvertierungen zu überprüfen, wählen Sie das für die Konvertierung verwendete PDF-Quelldokument aus und klicken Sie auf **Konvertierungen**&#x200B;überprüfen. Der Editor zum Überprüfen und Korrigieren wird in einer neuen Registerkarte geöffnet. Sie können mit der Überprüfung der Konversionen beginnen. Führen Sie die folgenden grundlegenden Überprüfungen vor der Behebung eines anderen Problems durch:

![](assets/usingreviewandcorrecteditor.png)

1. **Markieren Sie den Typ aller Felder**: Der Konvertierungsdienst kann einem Feld einen falschen Typ zuweisen. Geben Sie beispielsweise Text anstelle des Typs Telefon in das Handyfeld ein. Sie können den Mauszeiger auf ein Feld bewegen, um den Feldtyp zu suchen.

   Um den Typ eines Felds zu ändern, wählen Sie das Feld aus, öffnen Sie den Eigenschaftenbrowser, wählen Sie einen Wert aus der **[!UICONTROL Type]** Dropdown-Liste aus und tippen Sie auf **[!UICONTROL Save]**. Der Typ wird geändert.

   ![](assets/check-typex75.gif)

1. **Entfernen Sie zusätzliche Bedienfelder**: Der Konvertierungsdienst kann zusätzliche Bereiche generieren. Beispiel: Ein zusätzliches Unterfeld ist im übergeordneten Bedienfeld enthalten, leerer Raum wird in ein Bedienfeld umgewandelt, ein Kontrollkästchen wird in ein Bedienfeld umgewandelt. Überprüfen Sie die Begrenzungen aller Bereiche und entfernen Sie zusätzliche Bereiche. Sie können die Filterschaltfläche oder den ![](assets/toggle_eye.png) Inhaltsbrowser verwenden, um alle Bereiche anzuzeigen.

   Sie können ein Bedienfeld löschen oder die Gruppierung aufheben, um es zu entfernen. Bei Verwendung der Option zum Löschen werden auch die untergeordneten Felder oder Komponenten des Bedienfelds gelöscht:

   * Um ein Bedienfeld zu löschen, wählen Sie das Bedienfeld aus und tippen Sie in der Symbolleiste auf das Symbol zum Löschen ![](assets/delete-icon.png) . Tippen Sie im Bestätigungsdialogfeld auf **[!UICONTROL Confirm]**. Tap **[!UICONTROL Save]** to save the changes.

   * Um die Gruppierung eines Bedienfelds aufzuheben, wählen Sie das Bedienfeld aus und tippen Sie auf das Symbol &quot;Gruppierung aufheben&quot;in der Symbolleiste. Die Gruppierung des Bereichs wird aufgehoben, und untergeordnete Felder des nicht gruppierten Bereichs werden an das übergeordnete Feld angepasst. Tap **[!UICONTROL Save]**to save the changes.

1. **Erstellen Sie logische Textgruppen**: Validieren Sie die identifizierten Texte auf Vollständigkeit und Richtigkeit. Überprüfen Sie auch, dass die Texte logisch in die richtigen Bereiche oder Gruppen eingefügt werden. In einem mehrspaltigen Layout werden beispielsweise die Texte einer logischen Gruppe in eine andere Gruppe eingefügt.

   * Um Vollständigkeit und Richtigkeit des Textes zu überprüfen, verwenden Sie die ![](assets/toggle_eye.png) Schaltfläche &quot;Filter&quot;, um nur Text anzuzeigen, auf jeden Text zu klicken und zu validieren. Korrigieren Sie ggf. die Rechtschreibungs-, Tippfehler- oder Grammatikprobleme.

   * Um dem Formular Text hinzuzufügen, tippen Sie auf die Schaltfläche + und dann auf **[!UICONTROL Text]**. Zeichnen Sie das Feld, öffnen Sie den Eigenschaftenbrowser und geben Sie den Text ein, der dem Feld &quot;Inhalt&quot;hinzugefügt werden soll.

1. **** Überprüfungstabellen: Stellen Sie sicher, dass alle Tabellengrenzen identifiziert werden. Stellen Sie außerdem sicher, dass der Inhalt der Zellen korrekt identifiziert wird.

   * Verwenden Sie die **[!UICONTROL Add Column]** oder- **[!UICONTROL Add Row]** Option, um fehlende Ränder zu identifizieren.

   * Verwenden Sie zum Entfernen zusätzlicher Ränder die **[!UICONTROL Delete Column]** Option oder **[!UICONTROL Delete Row]** .

Nachdem Sie die erforderlichen Änderungen vorgenommen haben, tippen Sie auf die **[!UICONTROL Save & Convert]** Schaltfläche, um die PDF-Formulare an den Konvertierungsdienst erneut zu senden. Jedes Feld wird in eine entsprechende adaptive Feldkomponente konvertiert. Nach der Konvertierung werden die aktualisierten Elemente einschließlich des adaptiven Formulars und Schemas in Ihre AEM Forms-Instanz heruntergeladen. Je nach Komplexität des Formulars kann der Dienst einige Zeit in Anspruch nehmen, um die Konvertierung abzuschließen.

![Speichern und konvertieren](assets/save-and-convert.png)

Nachdem Sie die grundlegenden Prüfungen durchgeführt haben, können Sie das Formular überprüfen, um unternehmensspezifische Probleme zu beheben. Diese Probleme können mit dem Hinzufügen fehlender Felder und mehr zusammenhängen. In der Übersicht [Verwenden Sie die Werkzeuge](review-correct-ui-edited.md#use-the-review-and-correct-editor-tools) für den Review- und den Korrektur-Editor erfahren Sie mehr über alle Werkzeuge, die der Editor zur Behebung solcher Probleme bereitstellt.

Sie können auch daran arbeiten, identische Probleme zu erkennen, die in fast allen Ihren Formularen auftreten, und solche Muster an Adobe melden. Verwenden Sie den Editor Überprüfen und Korrigieren, bis das gewünschte Erlebnis erreicht ist.

## Verwenden der Werkzeuge zum Überprüfen und Korrigieren {#use-the-review-and-correct-editor-tools}

Mit dem Editor &quot;Review&quot;und &quot;Richtig&quot;können Sie:

* [Hinzufügen einer Komponente zum Formular](review-correct-ui-edited.md#add-a-component-to-the-form)
* [Hinzufügen oder Bearbeiten einer Tabelle](review-correct-ui-edited.md)
* [Typ einer Komponente ändern](review-correct-ui-edited.md#change-type-a-component)

* [Bedienfeld erstellen oder entfernen](review-correct-ui-edited.md#create-or-remove-a-panel)
* [Löschen eines Bereichs oder einer Komponente](review-correct-ui-edited.md#delete-a-panel-or-component)
* [Eigenschaften einer Komponente festlegen](review-correct-ui-edited.md#set-properties-of-a-component)
* [Formular zur Konvertierung senden](review-correct-ui-edited.md#send-a-form-for-conversion)

### Hinzufügen einer Komponente zum Formular {#add-a-component-to-the-form}

Der Konvertierungsdienst identifiziert möglicherweise einige Komponenten des Druckformulars nicht. Beispielsweise wird in einer Komponente **Geburtsdatum** eines Formulars während der Konvertierung nicht identifiziert. Sie können das **+** -Werkzeug verwenden, um solche Komponenten zu identifizieren. Mit dem Tool können Sie Text-, Feld-, Auswahlgruppe-, Tabellen- und Bereichskomponenten hinzufügen.

![](assets/add-component.gif)

Um dem Formular eine Komponente hinzuzufügen, tippen **[!UICONTROL +]** und tippen Sie auf **[!UICONTROL Field]**. Zeichnen Sie ein Feld mit Beschriftung und Eingabefeld des Felds. Beispielsweise verwendet das obige Beispielbild die Feldkomponente, um dem Formular die Beschriftung **Geburtsdatum** und das Feld Wert darunter hinzuzufügen. Wenn Sie das Feld zeichnen, identifiziert der Konvertierungsdienst den Typ des Felds. Sie können den Feldtyp bei Bedarf im Eigenschaftenbrowser ändern. Öffnen Sie nach dem Erstellen der Komponente den Eigenschaftenbrowser und legen Sie die Eigenschaften der Komponente fest.

Tippen Sie auf **[!UICONTROL Save]** &quot;Schaltfläche&quot;, um die Änderungen zu speichern, oder verwenden Sie die **[!UICONTROL Save & Convert]** Schaltfläche, um die PDF-Formulare an den Konvertierungsdienst erneut zu senden.

### Hinzufügen oder Bearbeiten einer Tabelle {#addedittable}

Bei der Konvertierung können einige Zellen, Begrenzungen oder Inhalte einer Tabellenzelle nicht identifiziert werden. Beispielsweise wird eine Tabellenzeile nicht identifiziert. Sie können diese Elemente mit dem Editor &quot;Review &amp; Correct&quot;identifizieren. Sie können für eine Tabelle die folgenden Aktionen ausführen:

* Um eine Tabelle auszuwählen, klicken Sie auf eine beliebige Tabellenzelle.
* Doppelklicken Sie auf eine Zelle, um die Eigenschaften einer Zelle wie Name, Titel oder Typ zu ändern. Sie können auch auf die Zelle doppelklicken, um den Inhalt zu ändern, ein Feld als erforderlich zu markieren und andere Eigenschaften auszuwählen.
* Verwenden Sie das **[!UICONTROL +]** Tool, um dem Formular eine vollständig nicht identifizierte oder neue Tabelle hinzuzufügen/zu identifizieren.
* Wenn Sie die Größe von Zellen oder Zeilen einer Tabelle ändern möchten, klicken Sie mit einem Klick auf den leeren Bereich der Tabelle, halten Sie den Mauszeiger über die Zeilen- oder Spaltengrenze und verschieben Sie die Begrenzung, wenn sich der Zeiger ändert. Nachdem Sie die Größe geändert haben, klicken Sie auf **[!UICONTROL Done]** , um die Änderungen zu übernehmen. Sie können die **[!UICONTROL ESC]** Taste drücken, um die Größe zu verwerfen.

* Um Zeilen oder Spalten hinzuzufügen oder zu löschen, wählen Sie eine Zelle in der Tabellenzeile aus und wählen Sie die **[!UICONTROL Add Row]**-, **[!UICONTROL Add Column]**- **[!UICONTROL Delete Row]** oder **[!UICONTROL Delete Column]** -Option im ![](assets/table_18x18.png) Menü aus.

* Um eine Zelle in eine Tabelle zu teilen, wählen Sie die **[!UICONTROL Spilt Vertical]** bzw. **[!UICONTROL Split Horizontal]** -Option aus dem ![](assets/table_18x18.png) Menü.

* Wenn Sie Zellen einer Tabelle zusammenführen möchten, wählen Sie die zusammenzuführenden Zellen aus und wählen Sie die **[!UICONTROL Merge Cells]** Option im ![](assets/table_18x18.png) Tabellenmenü aus.

### Typ einer Komponente ändern {#change-type-a-component}

Der Konvertierungsdienst kann einige Felder vom falschen Typ erstellen. In der folgenden Abbildung wird beispielsweise das Feld &quot; **Geschlecht** &quot;fälschlicherweise als **Textfeld** identifiziert. Außerdem ist der Inhalt der Beschriftung falsch. Das Feld sollte ein Auswahlfeldtyp sein, und die Beschriftung sollte &quot;Geschlecht&quot;lauten. So ändern Sie den Typ einer Komponente und korrigieren Sie ihre Beschriftung:

Wählen Sie das zu konvertierende Feld aus, tippen ![](assets/smock_shuffle_18_n.svg) und tippen Sie auf einen Feldtyp. Das Feld wird in den ausgewählten Feldtyp umgewandelt. Ein Feld kann nur in Typen konvertiert werden, die in der folgenden Tabelle aufgeführt sind. Eine Bereichskomponente kann nur aufgehoben, nicht transformiert werden.

| **Komponente** | **Konvertiert in** |
|---|---|
| Text | Feld- oder Auswahlgruppe |
| Feld | Text oder Auswahlgruppe |
| Auswahlgruppe | Text oder Bereich |

Öffnen Sie nach der Konvertierung den Eigenschaftenbrowser, geben Sie eine Beschriftung an und geben Sie andere erforderliche Eigenschaften an. Tippen Sie auf **[!UICONTROL Save]** , um die Änderungen zu speichern, oder verwenden Sie die Schaltfläche &quot;Speichern und konvertieren&quot;, um die PDF-Formulare an den Konvertierungsdienst erneut zu senden.

### Bedienfeld erstellen oder entfernen {#create-or-remove-a-panel}

Der Konvertierungsdienst aggregiert zugehörige Komponenten und Inhalte von Druckformularen in einem Bedienfeld. Das Formular kann beispielsweise einen Adressbereich mit Feldern wie z. B. Name, Plot-Nummer, Bereich, Stadt, Bundesland, Postleitzahl und Land haben. Diese Felder sind in einem Bedienfeld gruppiert. Ein Formular kann mehrere Bereiche haben.

Der Konvertierungsdienst kann Bereiche erstellen, die Komponenten ohne Beziehung zu anderen enthalten oder eine relative Komponente aus dem Bedienfeld ausschließen. Sie können die Werkzeuge zur Gruppe oder Aufhebung der Gruppierung verwenden, um diese Bereiche zu beheben:

* Um ein Bedienfeld zu entfernen, wählen Sie das Bedienfeld aus und tippen Sie auf ![Gruppierung aufheben](assets/ungroupX18.png). Das Bedienfeld wird entfernt und die untergeordneten Komponenten des Bedienfelds werden in die übergeordnete Komponente verschoben. Sie können auch die Option &quot;Komponente[ ](review-correct-ui-edited.md#delete-a-panel-or-component)löschen&quot;verwenden, um ein Bedienfeld und dessen untergeordnete Elemente zu löschen.

* Um ein Bedienfeld zu erstellen, verwenden Sie die Strg-Taste (unter Windows oder Linux) oder die Strg-Taste (unter Mac), um zugehörige Komponenten auszuwählen, und tippen Sie auf ![Gruppe](assets/group.jpg) , um ein Bedienfeld zu erstellen. Öffnen Sie den Eigenschaftenbrowser, um Eigenschaften des Bedienfelds anzugeben.

Tippen Sie auf **[!UICONTROL Save]** &quot;Schaltfläche&quot;, um die Änderungen zu speichern, oder verwenden Sie die **[!UICONTROL Save & Convert]** Schaltfläche, um die PDF-Formulare an den Konvertierungsdienst erneut zu senden.

### Löschen eines Bereichs oder einer Komponente {#delete-a-panel-or-component}

Der Konvertierungsdienst kann einige falsche Bereiche oder Komponenten identifizieren. Die meisten dieser Komponenten sind nicht miteinander verknüpft. Sie können diese Bereiche oder Komponenten löschen.

Um ein Bedienfeld oder eine Komponente zu löschen, wählen Sie ein Bedienfeld oder eine Komponente aus und tippen Sie auf das Löschen- ![](assets/delete-icon.png) Symbol. Tippen Sie im Bestätigungsdialogfeld auf **[!UICONTROL Confirm]**. Das ausgewählte Bedienfeld oder die ausgewählte Komponente wird gelöscht. Beim Löschen eines Bedienfelds werden auch alle untergeordneten Elemente des Bedienfelds gelöscht. Sie können die Strg-Taste (unter Windows oder Linux) oder die Strg-Taste (unter Mac) verwenden, um mehrere Komponenten oder Bereiche auszuwählen.

### Eigenschaften einer Komponente festlegen {#set-properties-of-a-component}

Jede Komponente des Formulars verfügt über eine Reihe von Eigenschaften wie Name, Titel, Typ. Um die Eigenschaften einer Komponente festzulegen, wählen Sie die Komponente aus und tippen Sie auf den Eigenschaftenbrowser. Die Eigenschaften der ausgewählten Komponente werden angezeigt. Ändern oder legen Sie die Eigenschaften fest.

Tippen Sie auf **[!UICONTROL Save]** &quot;Schaltfläche&quot;, um die Änderungen zu speichern, oder verwenden Sie die **[!UICONTROL Save & Convert]** Schaltfläche, um die PDF-Formulare an den Konvertierungsdienst erneut zu senden.

### Formular zur Konvertierung senden {#send-a-form-for-conversion}

Nachdem Sie alle erforderlichen Änderungen im Review- und Korrektur-Editor vorgenommen haben, können Sie das Formular zur Konvertierung erneut senden. Um das Formular zur Konvertierung zu senden, tippen Sie auf **[!UICONTROL Save & Convert]**. Das Quellformular **[!UICONTROL Sent for conversion label]** wird auf den Ordner angewendet, der das Quelldokument enthält, und das aktualisierte Quellformular wird in den Konvertierungsdienst hochgeladen, der auf der Adobe-E/A ausgeführt wird.

Je nach der Komplexität des Formulars kann es einige Zeit dauern, bis der Konvertierungsdienst das Formular konvertiert. Nach Abschluss der Konvertierung werden das konvertierte adaptive Formular und zugehörige Elemente auf Ihren Computer heruntergeladen. Sie können das Formular nach Abschluss der Konvertierung im Editor überprüfen und das adaptive Formular gegebenenfalls im [Editor](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html) für adaptive Formulare für den finalen Satz der Korrekturen öffnen.

Wenn Sie ein Formular zur Konvertierung erneut senden, nachdem Sie das Formular im Editor für adaptive Formulare aktualisiert haben, gehen alle im adaptiven Formular vorgenommenen Änderungen verloren. Sie können ein Formular nur nach erfolgreicher Konvertierung im Review- und im Korrektur-Editor öffnen.

<!--
Comment Type: draft

<h3>Open adaptive forms editor</h3>
-->

<!--
Comment Type: draft

<p>There can be instances where you require adaptive forms editor to make the changes like, applying a different theme to the form or fixing tables. Once you have made all the required changes in Review and Correct editor and converted the form, you can open your form in adaptive forms editor to make the final set of changes.</p>
<p>To open the form with adaptive forms editor, tap the <img src="assets/properties.png" /> icon, and tap <strong>Open Adaptive Form Editor</strong>. The form opens in adaptive form editor. </p>


## Previous {#previous}

[Use Automated Forms Conversion service](convert-existing-forms-to-adaptive-forms.md)
