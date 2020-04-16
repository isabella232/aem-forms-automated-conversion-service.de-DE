---
title: 'Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare '
seo-title: 'Fehlerbehebung beim Automatisierten Forms-Konvertierungsdienst (AFCS) '
description: 'Häufige AFCS-Probleme und ihre Lösungen '
seo-description: Häufige AFCS-Probleme und ihre Lösungen
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 4b9f3f4fe3b3901cb99c9374ff40e8f49855237f

---


# Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare


Der Artikel enthält Informationen zu Installations-, Konfigurations- und Verwaltungsproblemen, die in einer Umgebung des automatisierten Formularkonvertierungsdienstes auftreten können. Das Dokument enthält außerdem grundlegende Fehlerbehebungsschritte und Erläuterungen zu häufigen Fehlermeldungen.

## Häufige Fehler {#commonerrors}

| Fehler | Beispiel |
|--- |--- |
| **Fehlermeldung** <br> Die Kopfzeile des Zugriffstokens ist nicht verfügbar. <br><br>**Grund **<br>: Ein Administrator hat mehrere IMS-Konfigurationen erstellt, oder die IMS-Konfiguration kann den AFCS-Dienst in der Adobe Cloud nicht erreichen.<br><br>**Lösung** Wenn mehrere Konfigurationen vorhanden sind, löschen Sie alle Konfigurationen und <br> erstellen Sie eine neue Konfiguration [](configure-service.md#obtainpubliccertificates). <br> Wenn eine einzelne Konfiguration vorhanden ist, verwenden Sie diese **[!UICONTROL Health Check]** zur [Prüfung der Verbindung](configure-service.md#createintegrationoption). | ![Die Kopfzeile des Zugriffstokens steht nicht zur Verfügung](assets/invalid-ims-configuration.png) |
| **Fehlermeldung** Keine Verbindung mit dem Dienst möglich <br> .  <br><br>**Grund **<br>: In den Cloud-Diensten für den automatisierten Forms-Konvertierungsdienst werden falsche Dienst-URL oder keine Dienst-URL angegeben.<br><br>**Auflösungs** - <br> Korrekte [Dienst-URL](configure-service.md#configure-the-cloud-service) in den Diensten des Konvertierungsdienstes für automatisierte Formulare. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/wrong-endpoint-configured.png) |
| **Fehlermeldung** <br> Der Dienst konnte das Formular nicht konvertieren.  <br><br>**Grund **für<br>Probleme mit der Netzwerkverbindung am Ende oder wegen eines planmäßigen Wartungsvorgangs oder Ausfalls in der Adobe Cloud.<br><br>**Lösung** <br> Beheben Sie Probleme mit der Netzwerkverbindung am Ende und prüfen Sie den Status des Dienstes auf https://status.adobe.com/ auf geplante oder ungeplante Ausfälle. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/service-failure.png) |
| **Fehlermeldung** <br> Die Anzahl der Seiten ist größer als 15.  <br><br>**Grund **<br>: Der Ordner, der Quell-XDP- und PDF-Formulare enthält, enthält mehr als 15 Dateien.<br><br>**Auflösung** <br> : Stellen Sie sicher, dass die Anzahl der Formulare in einem Ordner kleiner als 15 ist. Bringen Sie die Gesamtanzahl der Seiten in einem Ordner unter 50. Vergrößern Sie den Ordner auf weniger als 10 MB. Speichern Sie Formulare nicht in einem Unterordner. Organisieren Sie Quelldateien in einem Dokumente von 8-15 Dokumenten. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/number-of-pages.png) |
| **Fehlermeldung** <br> Das Format der Quelldatei wird nicht unterstützt.  <br><br>**Grund **<br>: Der Ordner mit den Quellformularen enthält einige nicht unterstützte Dateien.<br><br>**Auflösung** <br> Der Dienst unterstützt nur .xdp- und .pdf-Dateien. Entfernen Sie Dateien mit einer anderen Erweiterung aus dem Ordner und führen Sie die Konvertierung aus. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/unsupported-file-formats.png) |
| **Fehlermeldung**<br> Gescannte Formulare werden nicht unterstützt.  <br><br>**Grund **<br>: Das PDF-Formular enthält nur ein gescanntes Bild des Formulars und keine Inhaltsstruktur.<br><br>**Auflösung** <br> Der Dienst unterstützt nicht die Konvertierung gescannter Formulare oder eines Formularbilds in ein vordefiniertes adaptives Formular. Sie können jedoch in Adobe Acrobat das Bild eines Formulars in ein PDF-Formular konvertieren. Verwenden Sie dann den Dienst, um das PDF-Formular in ein adaptives Formular zu konvertieren. Verwenden Sie für die Konvertierung in Acrobat immer ein qualitativ hochwertiges Bild des Formulars. Es verbessert die Qualität der Konvertierung. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/scanned-forms-error.png) |