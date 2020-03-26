---
title: 'Konvertieren von PDF-Formularen in adaptive Formulare '
seo-title: 'Konvertieren von PDF-Formularen in adaptive Formulare '
description: Ausführen des Dienstes zur automatischen Formularkonvertierung, um PDF-Formulare in adaptive Formulare zu konvertieren
seo-description: Ausführen des Dienstes zur automatischen Formularkonvertierung, um PDF-Formulare in adaptive Formulare zu konvertieren
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: bcd55fa59f37b71b95b7cbfd80fcda368eaba408

---


# Konvertieren von PDF-Formularen in adaptive Formulare{#convert-print-forms-to-adaptive-forms}

Der von Adobe Sensei unterstützte Dienst für die automatische Formularkonvertierung von AEM Forms konvertiert Ihre PDF-Formulare automatisch in gerätefreundliche und responsive adaptive Formulare. Unabhängig davon, ob Sie nicht-interaktive PDF-Formulare, Acro Forms oder XFA-basierte PDF-Formulare verwenden, kann der Dienst für die automatische Formularkonvertierung diese Formulare problemlos in adaptive Formulare konvertieren. Informationen zu den Funktionen, zum Konvertierungsablauf und zu Onboarding-Informationen finden Sie unter [Dienst für die automatische Formularkonvertierung](introduction.md).

## Voraussetzungen {#pre-requisites}

* [**Konvertierungsdienst konfigurieren **](configure-service.md)

* **Bereiten Sie die[Vorlagen](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html)vor, die auf konvertierte Formulare angewendet werden sollen:** Mithilfe einer Vorlage können Sie ein einheitliches Branding auf alle adaptiven Formulare anwenden. Darüber hinaus extrahiert und verwendet der Dienst für die automatische Formularkonvertierung keine Kopf- und Fußzeilen von Quell-PDF-Dokumenten. Sie können adaptive Formularvorlagen verwenden, um Kopf- und Fußzeilen anzugeben. In der Vorlage angegebene Kopf- und Fußzeilen werden während der Konvertierung auf die adaptiven Formulare angewendet.

* **Bereiten Sie die[Designs](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html)vor, die auf konvertierte Formulare angewendet werden sollen:** Mit einem Design können Sie einen einheitlichen Stil auf alle adaptiven Formulare Ihrer Organisation anwenden.

## Konvertierungsprozess starten{#start-the-conversion-process}

Nachdem Sie Ihre AEM-Instanz mit dem Dienst für die automatische Formularkonvertierung von AEM Forms verbunden haben, können Sie Ihre PDF-Formulare in adaptive Formulare konvertieren. Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um die Formulare zu konvertieren:

* [Laden Sie PDF-Formulare auf Ihren AEM Forms-Server hoch](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Führen Sie die Konvertierung aus](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Überprüfen und korrigieren Sie die konvertierten Formulare](review-correct-ui-edited.md)

### Laden Sie PDF-Formulare auf Ihren AEM Forms-Server hoch{#upload-pdf-forms-to-your-aem-forms-server}

Der Konvertierungsdienst konvertiert PDF-Formulare, die in Ihrer AEM Forms-Instanz verfügbar sind, in adaptive Formulare. Sie können alle PDF-Formulare je nach Bedarf gleichzeitig oder schrittweise hochladen. Beachten Sie vor dem Hochladen der Formulare Folgendes:

* Ein Ordner muss weniger als 15 Formulare und weniger als 50 Seiten enthalten.
* Die Größe des Ordners muss kleiner als 10 MB sein. Speichern Sie Formulare nicht in einem Unterordner.
* Ein Formular muss weniger als 15 Seiten umfassen.
* Laden Sie die geschützten Formulare nicht hoch. Der Dienst konvertiert keine kennwortgeschützten und gesicherten Formulare.
* Laden Sie keine Quellformulare mit Leerzeichen im Dateinamen hoch. Entfernen Sie das Leerzeichen aus dem Namen der Datei, bevor Sie die Formulare hochladen.
* Laden Sie keine [PDF-Portfolios](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)hoch. Der Dienst konvertiert keine PDF-Portfolios in adaptive Formulare.
* Lesen Sie die Abschnitte [Bekannte Probleme](known-issues.md) und [Best Practices und Überlegungen](styles-and-pattern-considerations-and-best-practices.md) und nehmen Sie die vorgeschlagenen Änderungen an den Formularen vor.

Führen Sie die folgenden Schritte aus, um die zu konvertierenden Formulare in einen in Ihrer AEM Forms-Instanz hochzuladen:

1. Melden Sie sich bei der AEM Forms-Instanz an.

1. Tap **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tippen Sie auf **[!UICONTROL Create]**> **[!UICONTROL Folder]**. Geben Sie **Titel** und **Name** des Ordners an. Tippen Sie auf **[!UICONTROL Create]**. Ein Ordner wird erstellt.
1. Tippen Sie darauf, um den neu erstellten Ordner zu öffnen.
1. Tippen Sie auf **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Select the forms to upload, click **[!UICONTROL Open]**, and click **[!UICONTROL Upload]**. Die Formulare werden hochgeladen.

### Führen Sie die Konvertierung aus {#run-the-conversion}

Führen Sie die folgenden Schritte aus, um die Konvertierung zu starten, nachdem Sie die Formulare hochgeladen und den Dienst konfiguriert haben:

1. Tippen Sie in Ihrer AEM Forms-Instanz auf **[!UICONTROL Adobe Experience Manager]** Konvertierungseinstellungen-Dialogfeld ![>](assets/adobeexperiencemanager.png) **[!UICONTROL Navigation]** > ![](assets/compass.png) > **[!UICONTROL Forms]** **[!UICONTROL Forms & Documents]**.
1. Select a form or the folder containing PDF forms (forms to be converted) and tap **[!UICONTROL Start Automated Conversion]**. The **[!UICONTROL Conversion Settings]** dialog appears.

   ![Geben Sie die Konfiguration an](assets/conversion-settings-dialog.png)

1. In the **[!UICONTROL Basic]** tab of the Conversion Settings dialog:

   * **[!UICONTROL Select a cloud configuration]**. Wenn Sie eine Konfiguration auswählen, sind Standardvorlage und -design bereits angegeben. Bei Bedarf können Sie eine andere Vorlage oder ein anderes Design angeben.
   * Geben Sie einen Speicherort an, an dem generierte adaptive Formulare und das entsprechende Design gespeichert werden sollen. Sie können Standardpfade verwenden oder benutzerdefinierte Pfade angeben.
   * Verwenden Sie die Option **Adaptive(s) Formular(e) ohne Datenbindungen generieren**, um auszuwählen, ob Sie ein adaptives Formular mit oder ohne Datenmodellbindung(en) generieren möchten.
Wenn Sie diese Option nicht auswählen, ordnet der Konvertierungsdienst das/die adaptive(n) Formular(e) automatisch einem JSON-Schema zu und erstellt eine Datenbindung zwischen den im adaptiven Formular und im JSON-Schema verfügbaren Feldern. Das **[!UICONTROL Save generated data model schema at]** Feld zeigt den Standardspeicherort zum Speichern des generierten JSON-Schemas an. Sie können den Speicherort auch anpassen, um das generierte Schema zu speichern.
Wenn Sie diese Option auswählen, generiert der Konvertierungsdienst ein adaptives Formular ohne Datenmodellbindungen. Nach einer erfolgreichen Konvertierung können Sie ein adaptives Formular einem Formulardatenmodell, einem XML-Schema oder einem JSON-Schema zuordnen. Weitere Informationen finden Sie unter [Erstellen eines adaptiven Formulars](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).
   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. In the **[!UICONTROL Additional]** tab of Conversion Settings dialog,
   * Select the **[!UICONTROL Extract fragment from adaptive forms]** option to allow the conversion service to identify, extract, and download form fragments for converted forms. When you select the **[!UICONTROL Extract fragment from adaptive forms]** option, the options to specify paths for saving extracted form fragments and corresponding form fragments schemas is enabled.
   * Specify the location of **[!UICONTROL existing adaptive form fragments]**, if you have some existing JSON schema based and schema less adaptive form fragments and you plan to use these fragments in automatically generated adaptive forms. Der Konvertierungsdienst stimmt verfügbare JSON-Schema-basierte und schemalose adaptive Formularfragmente mit eingegebenen PDF-Formularen ab (nur nicht-interaktive PDF-Formulare). Wenn eine Übereinstimmung vorliegt, wird das übereinstimmende adaptive Formularfragment in entsprechenden adaptiven Formularen verwendet.
   >[!NOTE]
   >
   >
   > * Sie können jeweils nur **[!UICONTROL  Extract Fragment]** oder nur **[!UICONTROL Use existing adaptive form fragments]** eine Option verwenden. Es ist nicht möglich, beide Optionen gleichzeitig zu verwenden.
   > * Sie können die **[!UICONTROL Use existing adaptive form fragments]** Option nur mit nicht interaktiven PDF-Formularen verwenden. Andere Formulartypen werden noch nicht unterstützt.
   > * Sie können nur ungebundene Fragmente oder an ein JSON-Schema gebundene Fragmente mit dem Dienst zur automatischen Konvertierung verwenden. Verwenden Sie keine XFA-Fragmente. XFA-Fragmente werden nicht unterstützt.


   * Wählen Sie die **[!UICONTROL Auto-detect multi-column layout of input forms]** Option, um das Layout des Quellformulars für große Bildschirme wie Desktop- und Laptop-Computer beizubehalten. Diese Option ist hilfreich, um das mehrspaltige Layout von Quellformularen beizubehalten. Wenn eine Quell-PDF-Datei beispielsweise ein zweispaltiges Layout aufweist, generiert der Dienst ein adaptives Ausgabeformular mit einem zweispaltigen Layout für große Bildschirme und einem einspaltigen Layout für Geräte mit kleinem Bildschirm wie Mobiltelefone. Die Funktion weist einige bekannte Probleme mit der Struktur des Datenquellenschemas auf. Weitere Informationen finden Sie im Artikel [Bekannte Probleme](known-issues.md).
   * Standardmäßig erstellt der Dienst für jede Seite eines PDF-Formulars einen eigenen Bereich auf der obersten Ebene. Mit der **[!UICONTROL Auto-detect logical sections]** Option können Sie jetzt Bedienfelder auf Seitenebene (auf Seitenzahlen basierende Bedienfelder) ablegen und nur logische Bedienfelder erstellen. Außerdem werden die Felder, die keinem Abschnitt zugeordnet sind, mit dem vorherigen logischen Abschnitt und die Felder eines logischen Abschnitts, die sich über zwei angrenzende Seiten verteilen, in einem einzigen logischen Abschnitt zusammengefasst. Wenn sich beispielsweise einige Felder eines logischen Abschnitts am Ende der ersten Seite und einige am Anfang der zweiten Seite befinden, werden alle diese Felder in einen einzigen logischen Abschnitt unterteilt.

      >[!NOTE]
      > Sie benötigen das Connector-Paket 1.1.38 oder höher, um die **[!UICONTROL Auto-detect logical sections]** Funktion verwenden zu können.



1. Tippen Sie auf **[!UICONTROL Start Conversion]**. Die Konvertierung wird gestartet. Der Konvertierungsfortschritt wird im Ordner oder im Formular angezeigt, bis die Konvertierung ausgeführt wird. Die Nachricht wird nach Abschluss der Konvertierung durch eine andere Statusmeldung ersetzt (konvertiert, teilweise konvertiert oder Konvertierung fehlgeschlagen). Nach Abschluss der Konvertierung wird auch eine Status-E-Mail an die konfigurierte E-Mail-Adresse gesendet:

   * On a successful conversion, the converted adaptive form and related schema are downloaded to the path specified in the **[!UICONTROL Basic]** tab of the conversion dialog. Formularfragmente und das entsprechende Schema werden nur heruntergeladen, wenn vor dem Start der Konvertierung die Option „Fragment extrahieren“ ausgewählt ist.
   * On a failed conversion, the **[!UICONTROL Conversion Failed]** message is displayed if all the input forms fail to convert or the **[!UICONTROL Partially Failed]** message is displayed when only a few of all the input forms fail to convert. Eine Status-E-Mail wird an die [konfigurierte E-Mail-Adresse ](configure-service.md#configureemailnotification) gesendet und ein Fehler in der Datei error.log protokolliert.
   Wenn Sie ein XFA-basiertes PDF-Formular in ein adaptives Formular konvertieren, ordnet der Konvertierungsdienst das PDF-Formular automatisch dem konvertierten adaptiven Formular als Datensatzdokumentvorlage zu. Nach der Konvertierung können Sie die Eigenschaften des adaptiven Formulars öffnen, um das Dokument der Datensatzvorlage im **[!UICONTROL Document of Record Template Configuration]** Bereich der **[!UICONTROL Form Model]** Registerkarte Ansicht. </br>

   Der Konvertierungsdienst lädt das PDF-Formular nur dann automatisch in das konvertierte adaptive Formular als Dokument der Datensatzvorlage hoch, wenn Sie die Option **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** > aktivieren.

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
   >Wenn der Konvertierungsprozess länger als 60 Minuten dauert und das PDF-Formular noch nicht in ein adaptives Formular konvertiert ist, erstellen Sie einen neuen Ordner in der AEM Forms-Instanz, laden Sie das PDF-Formular in den neu erstellten Ordner hoch und starten Sie die Konvertierung neu.

## Überprüfen und korrigieren Sie die konvertierten Formulare{#review-and-correct-the-converted-forms}

Formulare für die reale Welt stellen komplexe Anforderungen an die Datenerfassung dar. Sobald die automatische Konvertierung abgeschlossen ist, können Kunden die Konvertierungsqualität des Formulars überprüfen und die erforderlichen Aktualisierungen am Formular vornehmen. AEM Forms bietet einen Editor [Überprüfen und Korrigieren](review-correct-ui-edited.md), um die erforderlichen Änderungen vorzunehmen. Sie können die automatische Identifizierung von Formularfeldern verbessern und identifizierte Felder von einem Typ in einen anderen konvertieren. Sie können beispielsweise dazu beitragen, das zweispaltige Layout eines Formulars zu identifizieren und ein Feld, das automatisch als Optionsfeld identifiziert wird, in ein Mehrfachauswahlfeld zu ändern.
