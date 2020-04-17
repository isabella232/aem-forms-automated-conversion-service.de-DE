---
title: 'Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare '
seo-title: 'Fehlerbehebung beim Automatisierten Forms-Konvertierungsdienst (AFCS) '
description: 'Häufige AFCS-Probleme und ihre Lösungen '
seo-description: Häufige AFCS-Probleme und ihre Lösungen
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 3a82102feffa7fc618dc37c9a745c254a46a0700

---


# Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Häufige Fehler {#commonerrors}

| Fehler | Beispiel |
|--- |--- |
| **Fehlermeldung** <br> Die Kopfzeile des Zugriffstokens ist nicht verfügbar. <br><br> **Grund** <br> : Ein Administrator hat mehrere IMS-Konfigurationen erstellt, oder die IMS-Konfiguration kann den AFCS-Dienst in der Adobe Cloud nicht erreichen. <br><br>**Lösung **Wenn mehrere Konfigurationen vorhanden sind, löschen Sie alle Konfigurationen und<br>erstellen Sie eine neue Konfiguration[](configure-service.md#obtainpubliccertificates).<br>Wenn eine einzelne Konfiguration vorhanden ist, verwenden Sie** Health Check **, um die Verbindung zu[überprüfen](configure-service.md#createintegrationoption). | ![Die Kopfzeile des Zugriffstokens steht nicht zur Verfügung](assets/invalid-ims-configurations.png) |

| Fehler | Beispiel |
|--- |--- |
| **Fehlermeldung** Keine Verbindung mit dem Dienst möglich <br> .  <br><br>**Grund **<br>: In den Cloud-Diensten für den automatisierten Forms-Konvertierungsdienst werden falsche Dienst-URL oder keine Dienst-URL angegeben.<br><br>**Auflösungs** - <br> Korrekte [Dienst-URL](configure-service.md#configure-the-cloud-service) in den Diensten des Konvertierungsdienstes für automatisierte Formulare. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/wrong-endpoint-configured.png) |
| **Fehlermeldung** <br> Der Dienst konnte das Formular nicht konvertieren.  <br><br>**Da **<br>Probleme mit der Netzwerkverbindung am Ende auftreten, ist der Dienst aufgrund der geplanten Wartung oder des Ausfalls in der Adobe Cloud nicht verfügbar.<br><br>**Lösung** <br> Beheben Sie Probleme mit der Netzwerkverbindung am Ende und prüfen Sie den Status des Dienstes auf https://status.adobe.com/ auf einen geplanten oder ungeplanten Ausfall. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/service-failure.png) |
| **Fehlermeldung** <br> Die Anzahl der Seiten ist größer als 15.  <br><br>**Grund **<br>: Das Quellformular ist mehr als 15 Seiten lang.<br><br>**Auflösung** <br> Verwenden Sie Adobe Acrobat, um Formulare mit mehr als 15 Seiten zu teilen. Bringen Sie die Anzahl der Seiten in einem Formular auf unter 15. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/number-of-pages.png) |
| **Fehlermeldung** <br> Die Anzahl der Dateien ist größer als 15.  <br><br>**Grund **<br>: Der Ordner enthält mehr als 15 Formulare.<br><br>**Auflösung** <br> : Stellen Sie sicher, dass die Anzahl der Formulare in einem Ordner kleiner als 15 ist. Bringen Sie die Gesamtanzahl der Seiten in einem Ordner unter 50. Vergrößern Sie den Ordner auf weniger als 10 MB. Speichern Sie Formulare nicht in einem Unterordner. Organisieren Sie Quellformulare in einem Stapel von 8 bis 15 Formularen. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/number-of-pages.png) |
| **Fehlermeldung** <br> Das Format der Quelldatei wird nicht unterstützt.  <br><br>**Grund **<br>: Der Ordner mit den Quellformularen enthält einige nicht unterstützte Dateien.<br><br>**Auflösung** <br> Der Dienst unterstützt nur .xdp- und .pdf-Dateien. Entfernen Sie Dateien mit einer anderen Erweiterung aus dem Ordner und führen Sie die Konvertierung aus. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/unsupported-file-formats.png) |
| **Fehlermeldung**<br> Gescannte Formulare werden nicht unterstützt.  <br><br>**Grund **<br>: Das PDF-Formular enthält nur gescannte Bilder des Formulars und keine Inhaltsstruktur.<br><br>**Auflösung** <br> Der Dienst unterstützt nicht die Konvertierung gescannter Formulare oder eines Formularbilds in ein vordefiniertes adaptives Formular. Sie können jedoch in Adobe Acrobat das Bild eines Formulars in ein PDF-Formular konvertieren. Verwenden Sie dann den Dienst, um das PDF-Formular in ein adaptives Formular zu konvertieren. Verwenden Sie für die Konvertierung in Acrobat immer ein qualitativ hochwertiges Bild des Formulars. Es verbessert die Qualität der Konvertierung. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/scanned-forms-error.png) |
| **Das verschlüsselte PDF-Formular für Fehlermeldung** <br> wird nicht unterstützt.  <br><br>**Grund **<br>: Der Ordner enthält verschlüsselte PDF-Formulare.<br><br>**Auflösung** <br> Der Dienst unterstützt nicht die Konvertierung eines verschlüsselten PDF-Formulars in ein adaptives Formular. Entfernen Sie die Verschlüsselung, laden Sie das nicht verschlüsselte Formular hoch und führen Sie die Konvertierung aus. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/secured-pdf-form.png) |
| **Fehlermeldung** : JSON-Schema für Metamodell <br> kann nicht analysiert werden.  <br><br>**Grund **: Das<br>für den Dienst bereitgestellte JSON-Schema ist nicht korrekt formatiert, enthält ungültige Zeichen oder verwendet eine ungültige Syntax, um Komponenten zuzuordnen.<br><br>**Auflösung**<br> Überprüfen Sie die Formatierung der JSON-Datei. Sie können einen beliebigen Online-JSON-Validator verwenden, um die Formatierung und Struktur des Schemas zu überprüfen. Weitere Informationen zur Meta-Modell-Syntax finden Sie unter [Erweitern des standardmäßigen Artikels zum Meta-Modell](extending-the-default-meta-model.md) . | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/invalid-meta-model-schema.png) |

<!--

<table>
<thead>
<tr>
<th>Error</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Error Message</strong> <p> The access token header is not available. </p><br><strong>Reason</strong> <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br><strong>Resolution</strong> <br> If there are multiple configurations, delete all the configurations and <a href="configure-service.md#obtainpubliccertificates">create a new configuration</a>. <br> If there is a single configuration, use <strong> Health Check </strong> to <a href="configure-service.md#createintegrationoption">check connectivity</a>.</td>
<td><img alt="The access token header is not available" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service Cloud services.</td>
<td><img alt="Unable to connect to the service." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The service failed to convert the form.  <br><br><strong>Reason</strong> <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br><strong>Resolution</strong> <br> Resolve network connectivity issues at your end and check the status of the service on <a href="https://status.adobe.com/">https://status.adobe.com/</a> for a planned or unplanned outage.</td>
<td><img alt="The service failed to convert the form." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of pages is more than 15.  <br><br><strong>Reason</strong> <br> The source form is more than 15 pages long.  <br><br><strong>Resolution</strong> <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15.</td>
<td><img alt="The number of pages is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of files is more than 15.  <br><br><strong>Reason</strong> <br>  The folder contains more than 15 forms. <br><br><strong>Resolution</strong> <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms.</td>
<td><img alt="The number of files is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The source file format is not supported.  <br><br><strong>Reason</strong> <br> The folder containing source forms have some unsupported files. <br><br><strong>Resolution</strong> <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion.</td>
<td><img alt="The source file format is not supported." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Scanned forms are not supported.  <br><br><strong>Reason</strong> <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br><strong>Resolution</strong> <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion.</td>
<td><img alt="Scanned forms are not supported." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Encrypted PDF form is not supported.  <br><br><strong>Reason</strong> <br> The folder contains encrypted PDF forms. <br><br><strong>Resolution</strong> <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion.</td>
<td><img alt="Encrypted PDF form is not supported." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to parse meta-model JSON schema.  <br><br><strong>Reason</strong> <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br><strong>Resolution</strong> <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, <a href="extending-the-default-meta-model.md">Extend the default meta-model</a> article for information on meta-model syntax.</td>
<td><img alt="Unable to parse meta-model JSON schema" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
-->