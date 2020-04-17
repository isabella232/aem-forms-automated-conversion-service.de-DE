---
title: 'Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare '
seo-title: 'Fehlerbehebung beim Automatisierten Forms-Konvertierungsdienst (AFCS) '
description: 'Häufige AFCS-Probleme und ihre Lösungen '
seo-description: Häufige AFCS-Probleme und ihre Lösungen
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 56e4696c0372223e0b27f1c313382a2a637b6db1

---


# Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Häufige Fehler {#commonerrors}
<!--
|Error|Example|
|--- |--- |
|**Error Message** <br> The access token header is not available. <br><br>**Reason** <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br>**Resolution** <br> If there are multiple configurations, delete all the configurations and [create a new configuration](configure-service.md#obtainpubliccertificates). <br> If there is a single configuration, use **[!UICONTROL Health Check]** to [check connectivity](configure-service.md#createintegrationoption).|![The access token header is not available](assets/invalid-ims-configuration.png)|
|**Error Message** <br> Unable to connect to the service.  <br><br>**Reason** <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br>**Resolution** <br> Correct [Service URL](configure-service.md#configure-the-cloud-service) in Automated Forms Conversion Service Cloud services.|![Unable to connect to the service.](assets/wrong-endpoint-configured.png)|
|**Error Message** <br> The service failed to convert the form.  <br><br>**Reason** <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br>**Resolution** <br> Resolve network connectivity issues at your end and check the status of the service on https://status.adobe.com/ for a planned or unplanned outage.|![Unable to connect to the service.](assets/service-failure.png)|
|**Error Message** <br> The number of pages is more than 15.  <br><br>**Reason** <br> The source form is more than 15 pages long.  <br><br>**Resolution** <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15. |![Unable to connect to the service.](assets/number-of-pages.png)|
|**Error Message** <br> The number of files is more than 15.  <br><br>**Reason** <br>  The folder contains more than 15 forms. <br><br>**Resolution** <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms. |![Unable to connect to the service.](assets/number-of-pages.png)|
|**Error Message** <br> The source file format is not supported.  <br><br>**Reason** <br> The folder containing source forms have some unsupported files. <br><br>**Resolution** <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion. |![Unable to connect to the service.](assets/unsupported-file-formats.png)|
|**Error Message** <br> Scanned forms are not supported.  <br><br>**Reason** <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br>**Resolution** <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion. |![Unable to connect to the service.](assets/scanned-forms-error.png)|
|**Error Message** <br> Encrypted PDF form is not supported.  <br><br>**Reason** <br> The folder contains encrypted PDF forms. <br><br>**Resolution** <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion. |![Unable to connect to the service.](assets/secured-pdf-form.png)|
|**Error Message** <br> Unable to parse meta-model JSON schema.  <br><br>**Reason** <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br>**Resolution** <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, [Extend the default meta-model](extending-the-default-meta-model.md) article for information on meta-model syntax. |![Unable to connect to the service.](assets/invalid-meta-model-schema.png)| -->

<table>
<thead>
<tr>
<th>Fehler</th>
<th>Beispiel</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Fehlermeldung</strong> <br> Die Kopfzeile des Zugriffstokens ist nicht verfügbar. <br><br><strong>Grund</strong> <br> : Ein Administrator hat mehrere IMS-Konfigurationen erstellt, oder die IMS-Konfiguration kann den AFCS-Dienst in der Adobe Cloud nicht erreichen. <br><br><strong>Lösung</strong> Wenn mehrere Konfigurationen vorhanden sind, löschen Sie alle Konfigurationen und <br> erstellen Sie eine neue Konfiguration <a href="configure-service.md#obtainpubliccertificates"></a>. <br> Wenn eine einzelne Konfiguration vorhanden ist, verwenden Sie <strong>[!UICONTROL Health Check]</strong> , um die Verbindung <a href="configure-service.md#createintegrationoption">zu</a>überprüfen.</td>
<td><img alt="Die Kopfzeile des Zugriffstokens steht nicht zur Verfügung" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Fehlermeldung</strong> Keine Verbindung mit dem Dienst möglich <br> .  <br><br><strong>Grund</strong> <br> : In den Cloud-Diensten für den automatisierten Forms-Konvertierungsdienst werden falsche Dienst-URL oder keine Dienst-URL angegeben. <br><br><strong>Auflösungs</strong> - <br> Korrekte <a href="configure-service.md#configure-the-cloud-service">Dienst-URL</a> in den Diensten des Konvertierungsdienstes für automatisierte Formulare.</td>
<td><img alt="Verbindung zum Dienst kann nicht hergestellt werden." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Fehlermeldung</strong> <br> Der Dienst konnte das Formular nicht konvertieren.  <br><br><strong>Da</strong> <br> Probleme mit der Netzwerkverbindung am Ende auftreten, ist der Dienst aufgrund der geplanten Wartung oder des Ausfalls in der Adobe Cloud nicht verfügbar. <br><br><strong>Lösung</strong> Beheben Sie Probleme mit der Netzwerkverbindung am Ende und prüfen Sie den Status des Dienstes auf <br> https://status.adobe.com/ <a href="https://status.adobe.com/"></a> auf einen geplanten oder ungeplanten Ausfall.</td>
<td><img alt="Der Dienst konnte das Formular nicht konvertieren." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Fehlermeldung</strong> <br> Die Anzahl der Seiten ist größer als 15.  <br><br><strong>Grund</strong> <br> : Das Quellformular ist mehr als 15 Seiten lang.  <br><br><strong>Auflösung</strong> <br> Verwenden Sie Adobe Acrobat, um Formulare mit mehr als 15 Seiten zu teilen. Bringen Sie die Anzahl der Seiten in einem Formular auf unter 15.</td>
<td><img alt="Die Anzahl der Seiten beträgt mehr als 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Fehlermeldung</strong> <br> Die Anzahl der Dateien ist größer als 15.  <br><br><strong>Grund</strong> <br> : Der Ordner enthält mehr als 15 Formulare. <br><br><strong>Auflösung</strong> <br> : Stellen Sie sicher, dass die Anzahl der Formulare in einem Ordner kleiner als 15 ist. Bringen Sie die Gesamtanzahl der Seiten in einem Ordner unter 50. Vergrößern Sie den Ordner auf weniger als 10 MB. Speichern Sie Formulare nicht in einem Unterordner. Organisieren Sie Quellformulare in einem Stapel von 8 bis 15 Formularen.</td>
<td><img alt="Die Anzahl der Dateien ist größer als 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Fehlermeldung</strong> <br> Das Format der Quelldatei wird nicht unterstützt.  <br><br><strong>Grund</strong> <br> : Der Ordner mit den Quellformularen enthält einige nicht unterstützte Dateien. <br><br><strong>Auflösung</strong> <br> Der Dienst unterstützt nur .xdp- und .pdf-Dateien. Entfernen Sie Dateien mit einer anderen Erweiterung aus dem Ordner und führen Sie die Konvertierung aus.</td>
<td><img alt="Das Quelldateiformat wird nicht unterstützt." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Fehlermeldung</strong><br> Gescannte Formulare werden nicht unterstützt.  <br><br><strong>Grund</strong> <br> : Das PDF-Formular enthält nur gescannte Bilder des Formulars und keine Inhaltsstruktur. <br><br><strong>Auflösung</strong> <br> Der Dienst unterstützt nicht die Konvertierung gescannter Formulare oder eines Formularbilds in ein vordefiniertes adaptives Formular. Sie können jedoch in Adobe Acrobat das Bild eines Formulars in ein PDF-Formular konvertieren. Verwenden Sie dann den Dienst, um das PDF-Formular in ein adaptives Formular zu konvertieren. Verwenden Sie für die Konvertierung in Acrobat immer ein qualitativ hochwertiges Bild des Formulars. Es verbessert die Qualität der Konvertierung.</td>
<td><img alt="Gescannte Formulare werden nicht unterstützt." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Das verschlüsselte PDF-Formular für Fehlermeldung</strong> <br> wird nicht unterstützt.  <br><br><strong>Grund</strong> <br> : Der Ordner enthält verschlüsselte PDF-Formulare. <br><br><strong>Auflösung</strong> <br> Der Dienst unterstützt nicht die Konvertierung eines verschlüsselten PDF-Formulars in ein adaptives Formular. Entfernen Sie die Verschlüsselung, laden Sie das nicht verschlüsselte Formular hoch und führen Sie die Konvertierung aus.</td>
<td><img alt="Verschlüsseltes PDF-Formular wird nicht unterstützt." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Fehlermeldung</strong> : JSON-Schema für Metamodell <br> kann nicht analysiert werden.  <br><br><strong>Grund</strong> : Das <br> für den Dienst bereitgestellte JSON-Schema ist nicht korrekt formatiert, enthält ungültige Zeichen oder verwendet eine ungültige Syntax, um Komponenten zuzuordnen.  <br><br><strong>Auflösung</strong><br> Überprüfen Sie die Formatierung der JSON-Datei. Sie können einen beliebigen Online-JSON-Validator verwenden, um die Formatierung und Struktur des Schemas zu überprüfen. Weitere Informationen zur Meta-Modell-Syntax finden Sie unter <a href="extending-the-default-meta-model.md">Erweitern des standardmäßigen Artikels zum Meta-Modell</a> .</td>
<td><img alt="JSON-Schema mit Metadatenmodell kann nicht analysiert werden" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
