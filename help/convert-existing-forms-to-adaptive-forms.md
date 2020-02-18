---
title: 'Konvertieren von PDF-Formularen in adaptive Formulare '
seo-title: 'Konvertieren von PDF-Formularen in adaptive Formulare '
description: Führen Sie den Konvertierungsdienst für automatisierte Formulare aus, um PDF-Formulare in adaptive Formulare zu konvertieren
seo-description: Führen Sie den Konvertierungsdienst für automatisierte Formulare aus, um PDF-Formulare in adaptive Formulare zu konvertieren
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: bbf39e3bae55654f92a50f52a22cee5da938236d

---


# Konvertieren von PDF-Formularen in adaptive Formulare {#convert-print-forms-to-adaptive-forms}

Der automatisierte AEM Forms-Konvertierungsdienst für automatisierte Formulare mit Adobe Sensei konvertiert Ihre PDF-Formulare automatisch in gerätefreundliche und reaktionsfähige adaptive Formulare. Unabhängig davon, ob Sie nicht interaktive PDF-Formulare, Acro-Formulare oder XFA-basierte PDF-Formulare verwenden, der Automatisierte Forms-Konvertierungsdienst kann diese Formulare problemlos in adaptive Formulare konvertieren. Informationen zu den Funktionen, zum Konvertierungsarbeitsablauf und zu den Informationen zum Einstieg finden Sie unter [Automatisierte Formularkonvertierungsdienste](introduction.md) .

## Voraussetzungen {#pre-requisites}

* [**Konfigurieren des Konvertierungsdiensts **](configure-service.md)

* **[Vorbereitung der](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html)Vorlagen** , die auf konvertierte Formulare angewendet werden sollen: Mithilfe einer Vorlage können Sie konsistentes Branding auf alle adaptiven Formulare anwenden. Darüber hinaus extrahiert und verwendet der Automatisierte Forms-Konvertierungsdienst keine Kopf- und Fußzeile von PDF-Quelldokumenten. Sie können Vorlagen für adaptive Formulare verwenden, um Kopf- und Fußzeile anzugeben. Die in der Vorlage angegebenen Kopf- und Fußzeilen werden während der Konvertierung auf die adaptiven Formulare angewendet.

* **[Vorbereiten der](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html)Designs** , die auf konvertierte Formulare angewendet werden sollen: Mithilfe eines Designs können Sie einen konsistenten Stil auf alle adaptiven Formulare in Ihrem Unternehmen anwenden.

## Konvertierungsprozess starten {#start-the-conversion-process}

Nachdem Sie Ihre AEM-Instanz mit dem AEM Forms-Konvertierungsdienst verbunden haben, können Sie Ihre PDF-Formulare in adaptive Formulare konvertieren. Führen Sie die folgenden Schritte in der aufgeführten Reihenfolge aus, um die Formulare zu konvertieren:

* [Hochladen von PDF-Formularen auf den AEM Forms-Server](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Konvertierung ausführen](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Überprüfen und Korrigieren der konvertierten Formulare](review-correct-ui-edited.md)

### Hochladen von PDF-Formularen auf den AEM Forms-Server {#upload-pdf-forms-to-your-aem-forms-server}

Der Konvertierungsdienst konvertiert PDF-Formulare, die in Ihrer AEM Forms-Instanz verfügbar sind, in adaptive Formulare. Sie können bei Bedarf alle PDF-Formulare gleichzeitig oder in einem bestimmten Zeitabschnitt hochladen. Beachten Sie vor dem Hochladen der Formulare Folgendes:

* Halten Sie die Anzahl der Formulare in einem Ordner unter 15 und behalten Sie die Gesamtanzahl der Seiten in einem Ordner unter 50.
* Halten Sie die Größe des Ordners unter 10 MB. Speichern Sie keine Formulare in einem Unterordner.
* Halten Sie die Anzahl der Seiten in einem Formular unter 15.
* Laden Sie die geschützten Formulare nicht hoch. Der Dienst konvertiert keine kennwortgeschützten und geschützten Formulare.
* Laden Sie keine Quellformulare mit Leerzeichen im Dateinamen hoch. Entfernen Sie den Leerraum aus dem Namen der Datei, bevor Sie die Formulare hochladen.
* Laden Sie keine [PDF-Portfolios](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)hoch. Der Dienst konvertiert kein PDF-Portfolio in adaptive Formulare.
* Lesen Sie die Abschnitte [Bekannte Probleme](known-issues.md) und [Empfohlene Vorgehensweisen und Überlegungen](styles-and-pattern-considerations-and-best-practices.md) und nehmen Sie Vorschläge zu Änderungen an Formularen vor.

Führen Sie die folgenden Schritte aus, um die zu konvertierenden Formulare in einen Ordner in Ihrer AEM Forms-Instanz hochzuladen:

1. Melden Sie sich bei der AEM Forms-Instanz an.

1. Tap **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tippen Sie auf **[!UICONTROL Create]**> **[!UICONTROL Folder]**. Geben Sie **Titel** und **Name** des Ordners an. Tippen Sie auf **[!UICONTROL Create]**. Ein Ordner wird erstellt.
1. Tippen Sie auf , um den neu erstellten Ordner zu öffnen.
1. Tippen Sie auf **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Wählen Sie die hochzuladenden Formulare aus, klicken Sie auf **[!UICONTROL Open]** und klicken Sie auf **[!UICONTROL Upload]**. Die Formulare werden hochgeladen.

### Konvertierung ausführen {#run-the-conversion}

Nachdem Sie die Formulare hochgeladen und den Dienst konfiguriert haben, führen Sie die folgenden Schritte aus, um die Konvertierung zu starten:

1. Tippen Sie in Ihrer AEM Forms-Instanz auf **[!UICONTROL Adobe Experience Manager]** Konvertierungseinstellungen-Dialogfeld![ > ](assets/adobeexperiencemanager.png) **[!UICONTROL Navigation]** > ![](assets/compass.png) > **[!UICONTROL Forms]****[!UICONTROL Forms & Documents]**.
1. Wählen Sie ein Formular oder den Ordner mit PDF-Formularen (zu konvertierende Formulare) aus und tippen Sie auf **[!UICONTROL Start Automated Conversion]**. The **[!UICONTROL Conversion Settings]** dialog appears.

   ![Konfigurationen angeben](assets/conversion-settings-dialog.png)

1. Auf der **[!UICONTROL Basic]** Registerkarte des Dialogfelds Konvertierungseinstellungen:

   * **[!UICONTROL Select a cloud configuration]**. Wenn Sie eine Konfiguration auswählen, werden bereits die Standardvorlage und das Design angegeben. Sie können bei Bedarf eine andere Vorlage oder ein anderes Design angeben.
   * Geben Sie einen Speicherort für die erstellten adaptiven Formulare und das entsprechende Schema an. Sie können Standardpfade verwenden oder benutzerdefinierte Pfade angeben.
   * Verwenden Sie die Option &quot;Adaptive Formulare ohne Datenmodellbindung **erstellen&quot;** , um auszuwählen, ob Sie ein adaptives Formular mit oder ohne Datenmodellbindung(en) erstellen möchten.
Wenn Sie diese Option nicht auswählen, verknüpft der Konvertierungsdienst automatisch die adaptiven Formulare mit einem JSON-Schema und erstellt eine Datenbindung zwischen den im adaptiven Formular verfügbaren Feldern und dem JSON-Schema. Das **[!UICONTROL Save generated data model schema at]** Feld zeigt den Standardspeicherort zum Speichern des generierten JSON-Schemas an. Sie können den Speicherort auch anpassen, um das generierte Schema zu speichern.
Wenn Sie diese Option auswählen, generiert der Konvertierungsdienst ein adaptives Formular ohne Datenmodellbindungen. Nach einer erfolgreichen Konvertierung können Sie ein adaptives Formular mit einem Formulardatenmodell, einem XML-Schema oder einem JSON-Schema verknüpfen. For more information, see [Creating an adaptive form](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).
   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. Auf der **[!UICONTROL Additional]** Registerkarte &quot;Konvertierungseinstellungen&quot;wird
   * Wählen Sie die **[!UICONTROL Extract fragment from adaptive forms]** Option, damit der Konvertierungsdienst Formularfragmente für konvertierte Formulare identifizieren, extrahieren und herunterladen kann. Wenn Sie die **[!UICONTROL Extract fragment from adaptive forms]** Option auswählen, sind die Optionen zum Angeben von Pfaden zum Speichern von extrahierten Formularfragmenten und entsprechenden Formularfragmentschemata aktiviert.
   * Geben Sie den Speicherort für **[!UICONTROL existing adaptive form fragments]** die adaptiven Formularfragmente an, wenn Sie über vorhandene JSON-schemabasierte und schemabasierte Formularfragmente verfügen und diese Fragmente in automatisch erstellten adaptiven Formularen verwenden möchten. Der Konvertierungsdienst stimmt mit verfügbaren JSON-schemabasierten und schemabasierten adaptiven Formularfragmenten mit PDF-Eingabedateien überein (nur nicht interaktive PDF-Formulare). Wenn eine Übereinstimmung vorliegt, wird das entsprechende adaptive Formularfragment in den entsprechenden adaptiven Formularen verwendet.
   >[!NOTE]
   >
   >
   > * Sie können jeweils nur **[!UICONTROL  Extract Fragment]** oder nur **[!UICONTROL Use existing adaptive form fragments]** eine Option verwenden. Sie können beide Optionen nicht gleichzeitig verwenden.
   > * Sie können die **[!UICONTROL Use existing adaptive form fragments]** Option nur mit nicht interaktiven PDF-Formularen verwenden. Andere Formulartypen werden noch nicht unterstützt.
   > * Mit dem automatisierten Konvertierungsdienst können Sie nur ungebundene Fragmente oder Fragmente verwenden, die an ein JSON-Schema gebunden sind. Verwenden Sie keine XFA-Fragmente. XFA-Fragmente werden nicht unterstützt.


   * Wählen Sie die **[!UICONTROL Auto-detect multi-column layout of input forms]** Option, um das Layout des Quellformulars für große Bildschirme wie Desktop- und Laptop-Computer beizubehalten. Diese Option hilft beim Beibehalten des mehrspaltigen Layouts von Quellformularen. Wenn eine Quell-PDF beispielsweise ein zweispaltiges Layout hat, generiert der Dienst ein adaptives Formular für die Ausgabe mit einem zweispaltigen Layout für große Bildschirmanzeigen und einem einspaltigen Layout für kleine Bildschirme wie Mobiltelefone. Die Funktion weist einige bekannte Probleme mit der Datenquellen-Schemastruktur auf. Weitere Informationen finden Sie im Artikel zu [bekannten Problemen](known-issues.md) .



1. Tippen Sie auf **[!UICONTROL Start Conversion]**. Die Konvertierung wird gestartet. Der Konvertierungsstatus wird im Ordner oder im Formular angezeigt, bis die Konvertierung läuft. Die Nachricht wird nach Abschluss der Konvertierung durch eine weitere Statusmeldung ersetzt (Konvertierung, teilweise Konvertierung oder Konvertierung fehlgeschlagen). Nach Abschluss der Konvertierung wird auch eine Status-E-Mail an die konfigurierte E-Mail-Adresse gesendet:

   * Bei erfolgreicher Konvertierung werden das konvertierte adaptive Formular und das zugehörige Schema in den Pfad heruntergeladen, der auf der Registerkarte **[!UICONTROL Basic]** &quot;Konvertierungsdialogfeld&quot;angegeben ist. Formularfragmente und das zugehörige Schema werden nur heruntergeladen, wenn die Option &quot;Fragment extrahieren&quot;vor Beginn der Konvertierung ausgewählt ist.
   * Bei einer fehlgeschlagenen Konvertierung wird die **[!UICONTROL Conversion Failed]** Meldung angezeigt, wenn die Konvertierung aller Eingabefelder fehlgeschlagen ist oder die **[!UICONTROL Partially Failed]** Meldung angezeigt wird, wenn nur wenige der Eingabefelder die Konvertierung fehlschlagen. An die [konfigurierte E-Mail-Adresse](configure-service.md#configureemailnotification) wird eine Status-E-Mail gesendet und an die Datei &quot;error.log&quot;wird ein Fehler gemeldet.
   Wenn Sie ein XFA-basiertes PDF-Formular in ein adaptives Formular konvertieren, verknüpft der Konvertierungsdienst das PDF-Formular automatisch mit dem konvertierten adaptiven Formular als Datensatzdokument-Vorlage. Nach der Konvertierung können Sie die Eigenschaften des adaptiven Formulars öffnen, um die Vorlage &quot;Dokument aus Datensatz&quot;im **[!UICONTROL Document of Record Template Configuration]** Abschnitt der **[!UICONTROL Form Model]** Registerkarte anzuzeigen. </br>

   Der Konvertierungsdienst lädt das PDF-Formular nur dann automatisch als Datensatzdokument in das konvertierte adaptive Formular hoch, wenn Sie die Option **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** > aktivieren.

   <!--
   Comment Type: draft

   <note type="note">
   <p>By default, the adaptive form produces a JSON schema instead of XML schema on submission. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema. You can also use the following sample code for conversion:</p>
   <p><code class="code">import org.apache.sling.commons.json.JSONException;
   <discoiqbr /> import org.apache.sling.commons.json.JSONObject;
   <discoiqbr /> import org.apache.sling.commons.json.xml.XML;
   <discoiqbr />
   <discoiqbr /> public class ConversionUtils {
   <discoiqbr />
   <discoiqbr /> public static String jsonToXML(String jsonString) throws JSONException {
   <discoiqbr /> //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
   <discoiqbr /> //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
   <discoiqbr /> //Note: Need to extract boundData part before converting to XML
   <discoiqbr /> return XML.toString(new JSONObject(jsonString));
   <discoiqbr /> }
   <discoiqbr /> }</code><br /> </p>
   </note>
   -->

   >[!NOTE]
   >
   >Wenn der Konvertierungsprozess länger als 60 Minuten dauert und das PDF-Formular noch nicht in ein adaptives Formular konvertiert wird, erstellen Sie einen neuen Ordner in der AEM Forms-Instanz, laden Sie das PDF-Formular in den neu erstellten Ordner hoch und starten Sie die Konvertierung neu.

## Überprüfen und Korrigieren der konvertierten Formulare {#review-and-correct-the-converted-forms}

Echte Formulare haben komplexe Datenerfassungsanforderungen. Nach Abschluss der automatisierten Konvertierung können Kunden die Konvertierungsqualität des Formulars überprüfen und die erforderlichen Aktualisierungen am Formular vornehmen. AEM Forms bietet einen [Review- und einen richtigen](review-correct-ui-edited.md) Editor, um die erforderlichen Änderungen vorzunehmen. Dadurch können Sie die automatisierte Identifizierung von Formularfeldern verbessern und identifizierte Felder von einem Typ in einen anderen konvertieren. Sie können beispielsweise das zweispaltige Layout eines Formulars identifizieren und ein automatisch als Optionsfeld identifiziertes Feld in ein Feld mit mehreren Optionen ändern.
