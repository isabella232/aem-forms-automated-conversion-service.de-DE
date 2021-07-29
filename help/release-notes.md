---
title: Neuerungen? Versionshinweise - Dienst für die automatische Formularkonvertierung
description: Erfahren Sie mehr über die neuesten Funktionen und Fehler, die für den Dienst für die automatische Formularkonvertierung behoben wurden
exl-id: fccafbc9-28c1-4736-922c-24d675b25213
source-git-commit: 3f91fc0541f8fe8dbc997ae0b401c8a0a49347dd
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 96%

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

## 29. Juli 2021 (AFC-2021.07.2) {#july-2021}

* Es wurde eine Funktion hinzugefügt, mit der PDF forms in französischer, deutscher und spanischer Sprache in adaptive Formulare konvertiert werden kann.

## 24. Juni 2021 (AFC-2021.06.2) {#june-2021}

### Verbesserte Funktionen {#june-2021-improvements}

Verbesserte Genauigkeit bei der automatischen Erkennung logischer Abschnitte in den Quellformularen und Konvertieren dieser Abschnitte in entsprechende Bedienfelder adaptiver Formulare.

## 03. März 2021 (AFC-2021.02.2) {#mar-2021}

### Verbesserte Funktionen {#march-2021-improvements}

Verbesserungen beim Organisieren von Formularinhalten in Auswahlgruppen und Felder beim Konvertieren eines Quellformulars in ein adaptives Formular.

## 02. Februar 2021 (AFC-2021.01.2) {#feb-2021}

### Verbesserte Funktionen {#feb-2021-improvements}

Verbesserungen beim Organisieren von Formularinhalten in Bereichen und Erstellen von Bezeichnungen für Bereiche beim Konvertieren eines Quellformulars in ein adaptives Formular.

## 16. Juli 2020 (AFC-2020.07.2) {#jul-2020}

### Neue Funktionen {#whats-new-jul-2020-}

Zusätzliche Unterstützung für die Konvertierung farbiger PDF-Formulare in adaptive Formulare.

### Verbesserte Funktionen {#jul-2020-improvements}

Verbesserungen bei der automatischen Konvertierung von Text-, Formular- und Auswahlgruppenfeldern in entsprechende adaptive Formularkomponenten.


## 20. März 2020 (AFC-2020.03.1) {#mar-2020}

### Früher Zugang {#early-access}

**Logische Abschnitte in einem Formular automatisch erkennen**

Standardmäßig erstellt der Dienst für jede Seite eines PDF-Formulars ein separates Bedienfeld der obersten Ebene. Jetzt können Sie die Option **[!UICONTROL Logische Abschnitte automatisch erkennen]** verwenden, um Bereiche auf Seitenebene (Bereiche auf Seitenzahlbasis) zu löschen und nur logische Bereiche zu erstellen. Außerdem werden die Felder, die zu keinem Abschnitt mit dem vorhergehenden logischen Abschnitt gehören, und die Felder eines logischen Abschnitts, die auf zwei benachbarte Seiten verteilt sind, zu einem einzigen logischen Abschnitt zusammengefasst. Wenn sich beispielsweise einige Felder eines logischen Abschnitts am Ende von Seite eins und einige am Anfang von Seite zwei befinden, werden alle diese Felder in einem einzigen logischen Abschnitt zusammengefasst.

### Verbesserte Funktionen {#mar-2020-improvements}

**Verbesserungen bei der Listenerkennung**

Der Dienst erkennt jetzt Listen mit Aufzählungszeichen und Nummern effizienter.

### Spezielle Anweisungen {#special-instructions}

**Connector-Paket für den Dienst für die automatische Formularkonvertierung installieren**

Sie benötigen das Connector-Paket 1.1.38 oder höher, um die neuesten Funktionen und Verbesserungen der Version AFC-2020.03.1 nutzen zu können. Sie können das Connector-Paket von [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1) herunterladen.

Wenn Sie bereits über eine Umgebung des Dienstes für die automatische Formularkonvertierung verfügen, installieren Sie zur Verwendung der neuesten Funktionen des Konvertierungsdiensts das neueste Service Pack, das neueste Add-On-Paket für AEM Forms und das neueste Connector-Paket in der angegebenen Reihenfolge. Genaue Anweisungen finden Sie unter [Dienst zur automatischen Formularkonvertierung konfigurieren](configure-service.md).
