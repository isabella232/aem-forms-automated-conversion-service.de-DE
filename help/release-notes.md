---
title: Neuerungen? Versionshinweise - Dienst für die automatische Formularkonvertierung
description: 'Erfahren Sie mehr über die neuesten Funktionen und Fehler, die für den Dienst für die automatische Formularkonvertierung behoben wurden '
translation-type: ht
source-git-commit: 765f7bd4126fe4b8f4dd92c4b3eb556dae4e9ff0
workflow-type: ht
source-wordcount: '366'
ht-degree: 100%

---


# Versionshinweise

Dienst für die automatische Formularkonvertierung wird ständig verbessert. Besuchen Sie diese Seite regelmäßig, um über die neuesten Entwicklungen auf dem Laufenden zu bleiben. Diese Seite bietet Ihnen Informationen über:

* Früher Zugang
* Letzte Veröffentlichungen
* Neue Funktionen
* Verbesserungen
* Fehlerbehebungen
* Veraltete Funktionalität
* Spezielle Anweisungen
* Zukünftige Pläne für Änderungen

## 02. Februar 2021 (AFC-2021.01.2)

### Verbesserte Funktionen

Verbesserungen beim Organisieren von Formularinhalten in Bereichen und Erstellen von Bezeichnungen für Bereiche beim Konvertieren eines Quellformulars in ein adaptives Formular.

## 16. Juli 2020 (AFC-2020.07.2)

### Neue Funktionen

Zusätzliche Unterstützung für die Konvertierung farbiger PDF-Formulare in adaptive Formulare.

### Verbesserte Funktionen

Verbesserungen bei der automatischen Konvertierung von Text-, Formular- und Auswahlgruppenfeldern in entsprechende adaptive Formularkomponenten.


## 20. März 2020 (AFC-2020.03.1)

### Früher Zugang

**Logische Abschnitte in einem Formular automatisch erkennen**

Standardmäßig erstellt der Dienst für jede Seite eines PDF-Formulars ein separates Bedienfeld der obersten Ebene. Jetzt können Sie die Option **[!UICONTROL Logische Abschnitte automatisch erkennen]** verwenden, um Bereiche auf Seitenebene (Bereiche auf Seitenzahlbasis) zu löschen und nur logische Bereiche zu erstellen. Außerdem werden die Felder, die zu keinem Abschnitt mit dem vorhergehenden logischen Abschnitt gehören, und die Felder eines logischen Abschnitts, die auf zwei benachbarte Seiten verteilt sind, zu einem einzigen logischen Abschnitt zusammengefasst. Wenn sich beispielsweise einige Felder eines logischen Abschnitts am Ende von Seite eins und einige am Anfang von Seite zwei befinden, werden alle diese Felder in einem einzigen logischen Abschnitt zusammengefasst.

### Verbesserte Funktionen {#improvements}

**Verbesserungen bei der Listenerkennung**

Der Dienst erkennt jetzt Listen mit Aufzählungszeichen und Nummern effizienter.

### Spezielle Anweisungen

**Connector-Paket für den Dienst für die automatische Formularkonvertierung installieren**

Sie benötigen das Connector-Paket 1.1.38 oder höher, um die neuesten Funktionen und Verbesserungen der Version AFC-2020.03.1 nutzen zu können. Sie können das Connector-Paket von [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1) herunterladen.

Wenn Sie bereits über eine Umgebung des Dienstes für die automatische Formularkonvertierung verfügen, installieren Sie zur Verwendung der neuesten Funktionen des Konvertierungsdiensts das neueste Service Pack, das neueste Add-On-Paket für AEM Forms und das neueste Connector-Paket in der angegebenen Reihenfolge. Genaue Anweisungen finden Sie unter [Dienst zur automatischen Formularkonvertierung konfigurieren](configure-service.md).