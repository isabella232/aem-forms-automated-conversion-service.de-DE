---
title: 'Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare '
seo-title: 'Fehlerbehebung beim Automatisierten Forms-Konvertierungsdienst (AFCS) '
description: 'Häufige AFCS-Probleme und ihre Lösungen '
seo-description: Häufige AFCS-Probleme und ihre Lösungen
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: f8147653c9d0d0fbecfb06a7baa858f26a0406c4

---


# Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare


Der Artikel enthält Informationen zu Installations-, Konfigurations- und Verwaltungsproblemen, die in einer Umgebung des automatisierten Formularkonvertierungsdienstes auftreten können. Das Dokument enthält außerdem grundlegende Fehlerbehebungsschritte und Erläuterungen zu häufigen Fehlermeldungen.

## Häufige Fehler {#commonerrors}

| Fehler | Beispiel |
|--- |--- |
| **Fehlermeldung** <br> Die Kopfzeile des Zugriffstokens ist nicht verfügbar. <br><br>**Grund **<br>: Ein Administrator hat mehrere IMS-Konfigurationen erstellt, oder die IMS-Konfiguration kann den AFCS-Dienst in der Adobe Cloud nicht erreichen.<br><br>**Lösung** Wenn mehrere Konfigurationen vorhanden sind, löschen Sie alle Konfigurationen und <br> erstellen Sie eine neue Konfiguration [](configure-service.md#obtainpubliccertificates). <br> Wenn eine einzelne Konfiguration vorhanden ist, verwenden Sie diese **[!UICONTROL Health Check]** zur [Prüfung der Verbindung](configure-service.md#createintegrationoption). | ![Die Kopfzeile des Zugriffstokens steht nicht zur Verfügung](assets/invalid-ims-configuration.png) |
| **Fehlermeldung** Keine Verbindung mit dem Dienst möglich <br> .  <br><br>**Grund **<br>: In den Cloud-Diensten für den automatisierten Forms-Konvertierungsdienst werden falsche Dienst-URL oder keine Dienst-URL angegeben.<br><br>**Auflösungs** - <br> Korrekte [Dienst-URL](configure-service.md#configure-the-cloud-service) in den Diensten des Konvertierungsdienstes für automatisierte Formulare. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/wrong-endpoint-configured.png) |
| **Fehlermeldung** Keine Verbindung mit dem Dienst möglich <br> .  <br><br>**Grund **<br>: In den Cloud-Diensten für den automatisierten Forms-Konvertierungsdienst werden falsche Dienst-URL oder keine Dienst-URL angegeben.<br><br>**Auflösungs** - <br> Korrekte [Dienst-URL](configure-service.md#configure-the-cloud-service) in den Diensten des Konvertierungsdienstes für automatisierte Formulare. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/wrong-endpoint-configured.png) |
