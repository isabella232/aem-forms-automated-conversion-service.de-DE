---
title: 'Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare '
seo-title: 'Fehlerbehebung beim Automatisierten Forms-Konvertierungsdienst (AFCS) '
description: 'Häufige AFCS-Probleme und ihre Lösungen '
seo-description: Häufige AFCS-Probleme und ihre Lösungen
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 0af626e21a0c3d6a7d3c339c0b87179b048092d3

---


# Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Häufige Fehler {#commonerrors}

<table>
<thead>
<tr>
<th>Fehler</th>
<th>Beispiel</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Fehlermeldung</strong> <br> Die Kopfzeile des Zugriffstokens ist nicht verfügbar. <br><br><strong>Grund</strong> <br> : Ein Administrator hat mehrere IMS-Konfigurationen erstellt, oder die IMS-Konfiguration kann den AFCS-Dienst in der Adobe Cloud nicht erreichen. <br><br><strong>Lösung</strong> Wenn mehrere Konfigurationen vorhanden sind, löschen Sie alle Konfigurationen und <br> erstellen Sie eine neue Konfiguration <a href="configure-service.md#obtainpubliccertificates"></a>. <br> Wenn eine einzelne Konfiguration vorhanden ist, verwenden Sie <strong> Health Check </strong> , um die Verbindung zu <a href="configure-service.md#createintegrationoption">überprüfen</a>.</td>
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
