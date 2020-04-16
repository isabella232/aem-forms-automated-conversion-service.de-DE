---
title: 'Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare '
seo-title: 'Fehlerbehebung beim Automatisierten Forms-Konvertierungsdienst (AFCS) '
description: 'Häufige AFCS-Probleme und ihre Lösungen '
seo-description: Häufige AFCS-Probleme und ihre Lösungen
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: ccf30bc990c1a7cdb261332403668af6f35aeb9e

---


# Fehlerbehebung beim Konvertierungsdienst für automatisierte Formulare


Der Artikel enthält Informationen zu Installations-, Konfigurations- und Verwaltungsproblemen, die in einer Umgebung des automatisierten Formularkonvertierungsdienstes auftreten können. Das Dokument enthält außerdem grundlegende Fehlerbehebungsschritte und Erläuterungen zu häufigen Fehlermeldungen.

## Häufige Fehler {#commonerrors}

| Fehler | Beispiel |
|--- |--- |
| **Fehlermeldung** <br> Die Kopfzeile des Zugriffstokens ist nicht verfügbar. <br><br>**Grund **<br>: Ein Administrator hat mehrere IMS-Konfigurationen erstellt, oder die IMS-Konfiguration kann den AFCS-Dienst in der Adobe Cloud nicht erreichen.<br><br>**Lösung** Wenn mehrere Konfigurationen vorhanden sind, löschen Sie alle Konfigurationen und <br> erstellen Sie eine neue Konfiguration [](configure-service.md#obtainpubliccertificates). <br> Wenn eine einzelne Konfiguration vorhanden ist, verwenden Sie diese **[!UICONTROL Health Check]** zur [Prüfung der Verbindung](configure-service.md#createintegrationoption). | ![Die Kopfzeile des Zugriffstokens steht nicht zur Verfügung](assets/invalid-ims-configuration.png) |
| **Fehlermeldung** Keine Verbindung mit dem Dienst möglich <br> .  <br><br>**Grund **<br>: In den Cloud-Diensten für den automatisierten Forms-Konvertierungsdienst werden falsche Dienst-URL oder keine Dienst-URL angegeben.<br><br>**Auflösungs** - <br> Korrekte [Dienst-URL](configure-service.md#configure-the-cloud-service) in den Diensten des Konvertierungsdienstes für automatisierte Formulare. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/wrong-endpoint-configured.png) |
| **Fehlermeldung** <br> Der Dienst konnte das Formular nicht konvertieren.  <br><br>**Grund **für<br>Probleme mit der Netzwerkverbindung am Ende oder wegen eines planmäßigen Wartungsvorgangs oder Ausfalls in der Adobe Cloud.<br><br>**Lösung** <br> Beheben Sie Probleme mit der Netzwerkverbindung am Ende und prüfen Sie den Status des Dienstes auf https://status.adobe.com/# auf geplante oder ungeplante Ausfälle. | ![Verbindung zum Dienst kann nicht hergestellt werden.](assets/service-failure.png) |
