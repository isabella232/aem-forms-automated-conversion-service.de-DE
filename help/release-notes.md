---
title: Neuerungen? Versionshinweise - Automatisierter Forms-Konvertierungsdienst
description: 'Erfahren Sie mehr über die neuesten Funktionen und den Fehler, der für den automatisierten Forms-Konvertierungsdienst behoben wurde '
translation-type: tm+mt
source-git-commit: e88b9606878cb408c0369b5f20a644db93578f64

---


# Automatisierter Forms-Konvertierungsdienst: Versionshinweise

Der automatisierte Forms-Konvertierungsdienst wird laufend verbessert. Um sich über die neuesten Entwicklungen auf dem Laufenden zu halten, besuchen Sie diese Seite regelmäßig. Auf dieser Seite finden Sie Informationen zu folgenden Themen:

* Neueste Versionen
* Neue Funktionen
* Fehlerbehebungen
* Veraltete Funktionalität
* Besondere Hinweise
* Künftige Änderungspläne

Diese Seite wird monatlich aktualisiert. Besuchen Sie sie daher regelmäßig erneut.

## 20. März 2020 (AFC-2020.03.1)

### Neuerungen

**Automatische Erkennung von logischen Abschnitten in einem Formular**

Standardmäßig erstellt der Dienst für jede Seite eines PDF-Eingabedatums einen eigenen Bereich auf der obersten Ebene. Jetzt können Sie die **[!UICONTROL Auto-detect logical sections]** Option auswählen, um die Vorstellung zu entfernen, dass für jede PDF-Seite ein separates Bedienfeld auf der obersten Ebene erstellt und logische Abschnitte automatisch erkannt werden. Die Service Clubs verknüpften Felder eines Formulars mit einem logischen Abschnitt. Beispielsweise werden alle mit der Rechnungsadresse zusammenhängenden Felder in einen Abschnitt unterteilt und alle mit der Lieferadresse zusammenhängenden Felder in einen anderen Abschnitt unterteilt. Der Dienst erstellt für jeden automatisch erkannten logischen Abschnitt auch einen eigenen Bereich auf der obersten Ebene.

### Verbesserte Funktionen

**Verbesserungen bei der Erkennung von Listen**

Der Dienst ist jetzt beim Erkennen von Listen mit Aufzählungszeichen und Nummerierungen effizienter. Es kann jetzt Listen auf mehreren Ebenen leicht erkennen.

### Besondere Hinweise

**Automatisches Forms Conversion Service Connector-Paket installieren**

Sie benötigen das Connector-Paket 1.1.38 oder höher, um die neuesten Funktionen und Verbesserungen zu verwenden, die in Version AFC-2020.03.1 bereitgestellt wurden. Sie können das Connector-Paket von [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/fd/AEM-Forms-6.5.4.0-WIN)herunterladen.

Wenn Sie bereits über eine Umgebung des automatisierten Forms-Konvertierungsdiensts verfügen, installieren Sie zur Verwendung der neuesten Funktionen des Konvertierungsdiensts das neueste Service Pack, das neueste Add-On-Paket für AEM Forms und das neueste Connector-Paket in der oben genannten Reihenfolge. For detailed instructions, see the [Configure the Automated Forms Conversion service](configure-service.md) article.
