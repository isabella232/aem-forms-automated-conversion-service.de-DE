---
title: Neuerungen? Versionshinweise - Automatisierter Forms-Konvertierungsdienst
description: 'Erfahren Sie mehr über die neuesten Funktionen und den Fehler, der für den automatisierten Forms-Konvertierungsdienst behoben wurde '
translation-type: tm+mt
source-git-commit: c0ca850a0a1e82e34364766601011d6367b218ac

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

Standardmäßig erstellt der Dienst für jede Seite eines PDF-Formulars einen eigenen Bereich auf der obersten Ebene. Mit der **[!UICONTROL Auto-detect logical sections]** Option können Sie jetzt Bedienfelder auf Seitenebene (auf Seitenzahlen basierende Bedienfelder) ablegen und nur logische Bedienfelder erstellen. Außerdem werden die Felder, die nicht zu einem Abschnitt mit vorhergehender logischer Ausrichtung gehören, und die Felder eines logischen Abschnitts, die sich über zwei angrenzende Seiten erstrecken, in einen einzigen logischen Abschnitt zusammengefasst. Wenn sich beispielsweise einige Felder eines logischen Abschnitts am Ende der ersten Seite und einige am Anfang der zweiten Seite befinden, werden alle diese Felder in einen einzigen logischen Abschnitt unterteilt.

### Verbesserte Funktionen

**Verbesserungen bei der Erkennung von Listen**

Der Dienst ist jetzt beim Erkennen von Listen mit Aufzählungszeichen und Nummerierungen effizienter.

### Besondere Hinweise

**Automatisches Forms Conversion Service Connector-Paket installieren**

Sie benötigen das Connector-Paket 1.1.38 oder höher, um die neuesten Funktionen und Verbesserungen zu verwenden, die in Version AFC-2020.03.1 bereitgestellt wurden. Sie können das Connector-Paket von [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1)herunterladen.

Wenn Sie bereits über eine Umgebung des automatisierten Forms-Konvertierungsdiensts verfügen, installieren Sie zur Verwendung der neuesten Funktionen des Konvertierungsdiensts das neueste Service Pack, das neueste Add-On-Paket für AEM Forms und das neueste Connector-Paket in der angegebenen Reihenfolge. For detailed instructions, see the [Configure the Automated Forms Conversion service](configure-service.md) article.