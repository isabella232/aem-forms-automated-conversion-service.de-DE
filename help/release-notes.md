---
title: Neuerungen? Versionshinweise - Automatisierter Forms-Konvertierungsdienst
description: 'Erfahren Sie mehr über die neuesten Funktionen und den Fehler, der für den automatisierten Forms-Konvertierungsdienst behoben wurde '
translation-type: tm+mt
source-git-commit: dc17dfcb331df6144b8a7ce3c9c9d840b1182a95

---


# Automatisierter Forms-Konvertierungsdienst: Versionshinweise

Der automatisierte Forms-Konvertierungsdienst wird laufend verbessert. Um sich über die neuesten Entwicklungen auf dem Laufenden zu halten, besuchen Sie diese Seite regelmäßig. Auf dieser Seite finden Sie Informationen zu folgenden Themen:

* Vorzeitiger Zugriff
* Neueste Versionen
* Neue Funktionen
* verbessert
* Fehlerbehebungen
* Veraltete Funktionalität
* Besondere Hinweise
* Künftige Änderungspläne

## 20. März 2020 (AFC-2020.03.1)

### Vorzeitiger Zugriff

**Automatische Erkennung von logischen Abschnitten in einem Formular**

AFC-2020.03.1 Version bietet frühzeitigen Zugriff auf die **[!UICONTROL Auto-detect logical sections]** Funktion.

Standardmäßig erstellt der Dienst für jede Seite eines PDF-Formulars einen eigenen Bereich auf der obersten Ebene. Mit der **[!UICONTROL Auto-detect logical sections]** Option können Sie jetzt Bedienfelder auf Seitenebene (auf Seitenzahlen basierende Bedienfelder) ablegen und nur logische Bedienfelder erstellen.  Außerdem werden die Felder, die keinem Abschnitt zugeordnet sind, mit dem vorherigen logischen Abschnitt und die Felder eines logischen Abschnitts, die sich über zwei angrenzende Seiten verteilen, in einem einzigen logischen Abschnitt zusammengefasst. Wenn sich beispielsweise einige Felder eines logischen Abschnitts am Ende der ersten Seite und einige am Anfang der zweiten Seite befinden, werden alle diese Felder in einen einzigen logischen Abschnitt unterteilt.

Sie benötigen das Connector-Paket 1.1.38 oder höher, um die **[!UICONTROL Auto-detect logical sections]** Funktion verwenden zu können. You can download the connector package from [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

### Verbesserte Funktionen

**Verbesserungen bei der Erkennung von Listen**

Der Dienst ist jetzt beim Erkennen von Listen mit Aufzählungszeichen und Nummerierungen effizienter.