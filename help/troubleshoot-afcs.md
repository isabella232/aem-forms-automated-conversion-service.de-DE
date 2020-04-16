---
title: 'Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare '
seo-title: 'Fehlerbehebung beim Automatisierten Forms-Konvertierungsdienst (AFCS) '
description: 'Häufige AFCS-Probleme und ihre Lösungen '
seo-description: Häufige AFCS-Probleme und ihre Lösungen
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 74ff988f097ae3ea90c802c8884a78ba330fcf58

---


# Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Häufige Fehler {#commonerrors}

| Fehler | Beispiel |
|--- |--- |
| **Fehlermeldung** <br> Die Kopfzeile des Zugriffstokens ist nicht verfügbar. <br><br>**Grund **<br>: Ein Administrator hat mehrere IMS-Konfigurationen erstellt, oder die IMS-Konfiguration kann den AFCS-Dienst in der Adobe Cloud nicht erreichen.<br><br>**Lösung** Wenn mehrere Konfigurationen vorhanden sind, löschen Sie alle Konfigurationen und <br> erstellen Sie eine neue Konfiguration [](configure-service.md#obtainpubliccertificates). <br> Wenn eine einzelne Konfiguration vorhanden ist, verwenden Sie diese **[!UICONTROL Health Check]** zur [Prüfung der Verbindung](configure-service.md#createintegrationoption). | ![Die Kopfzeile des Zugriffstokens steht nicht zur Verfügung](assets/invalid-ims-configuration.png) |
| **Fehlermeldung** Keine Verbindung mit dem Dienst möglich <br> .  <br><br>**Grund **<br>: In den Cloud-Diensten für den automatisierten Forms-Konvertierungsdienst werden falsche Dienst-URL oder keine Dienst-URL angegeben.<br><br>**Auflösungs** - <br> Korrekte [Dienst-URL](configure-service.md#configure-the-cloud-service) in den Diensten des Konvertierungsdienstes für automatisierte Formulare. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/wrong-endpoint-configured.png) |
| **Fehlermeldung** <br> Der Dienst konnte das Formular nicht konvertieren.  <br><br>**Da **<br>Probleme mit der Netzwerkverbindung am Ende auftreten, ist der Dienst aufgrund der geplanten Wartung oder des Ausfalls in der Adobe Cloud nicht verfügbar.<br><br>**Lösung** <br> Beheben Sie Probleme mit der Netzwerkverbindung am Ende und prüfen Sie den Status des Dienstes auf https://status.adobe.com/ auf einen geplanten oder ungeplanten Ausfall. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/service-failure.png) |
| **Fehlermeldung** <br> Die Anzahl der Seiten ist größer als 15.  <br><br>**Grund **<br>: Das Quellformular ist mehr als 15 Seiten lang.<br><br>**Auflösung** <br> Verwenden Sie Adobe Acrobat, um Formulare mit mehr als 15 Seiten zu teilen. Bringen Sie die Anzahl der Seiten in einem Formular auf unter 15. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/number-of-pages.png) |
| **Fehlermeldung** <br> Die Anzahl der Dateien ist größer als 15.  <br><br>**Grund **<br>: Der Ordner enthält mehr als 15 Formulare.<br><br>**Auflösung** <br> : Stellen Sie sicher, dass die Anzahl der Formulare in einem Ordner kleiner als 15 ist. Bringen Sie die Gesamtanzahl der Seiten in einem Ordner unter 50. Vergrößern Sie den Ordner auf weniger als 10 MB. Speichern Sie Formulare nicht in einem Unterordner. Organisieren Sie Quellformulare in einem Stapel von 8 bis 15 Formularen. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/number-of-pages.png) |
| **Fehlermeldung** <br> Das Format der Quelldatei wird nicht unterstützt.  <br><br>**Grund **<br>: Der Ordner mit den Quellformularen enthält einige nicht unterstützte Dateien.<br><br>**Auflösung** <br> Der Dienst unterstützt nur .xdp- und .pdf-Dateien. Entfernen Sie Dateien mit einer anderen Erweiterung aus dem Ordner und führen Sie die Konvertierung aus. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/unsupported-file-formats.png) |
| **Fehlermeldung**<br> Gescannte Formulare werden nicht unterstützt.  <br><br>**Grund **<br>: Das PDF-Formular enthält nur gescannte Bilder des Formulars und keine Inhaltsstruktur.<br><br>**Auflösung** <br> Der Dienst unterstützt nicht die Konvertierung gescannter Formulare oder eines Formularbilds in ein vordefiniertes adaptives Formular. Sie können jedoch in Adobe Acrobat das Bild eines Formulars in ein PDF-Formular konvertieren. Verwenden Sie dann den Dienst, um das PDF-Formular in ein adaptives Formular zu konvertieren. Verwenden Sie für die Konvertierung in Acrobat immer ein qualitativ hochwertiges Bild des Formulars. Es verbessert die Qualität der Konvertierung. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/scanned-forms-error.png) |
| **Das verschlüsselte PDF-Formular für Fehlermeldung** <br> wird nicht unterstützt.  <br><br>**Grund **<br>: Der Ordner enthält verschlüsselte PDF-Formulare.<br><br>**Auflösung** <br> Der Dienst unterstützt nicht die Konvertierung eines verschlüsselten PDF-Formulars in ein adaptives Formular. Entfernen Sie die Verschlüsselung, laden Sie das nicht verschlüsselte Formular hoch und führen Sie die Konvertierung aus. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/secured-pdf-form.png) |
| **Fehlermeldung** : JSON-Schema für Metamodell <br> kann nicht analysiert werden.  <br><br>**Grund **: Das<br>für den Dienst bereitgestellte JSON-Schema ist nicht korrekt formatiert, enthält ungültige Zeichen oder verwendet eine ungültige Syntax, um Komponenten zuzuordnen.<br><br>**Auflösung**<br> Überprüfen Sie die Formatierung der JSON-Datei. Sie können einen beliebigen Online-JSON-Validator verwenden, um die Formatierung und Struktur des Schemas zu überprüfen. Weitere Informationen zur Meta-Modell-Syntax finden Sie unter [Erweitern des standardmäßigen Artikels zum Meta-Modell](extending-the-default-meta-model.md) . | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/invalid-meta-model-schema.png) |
