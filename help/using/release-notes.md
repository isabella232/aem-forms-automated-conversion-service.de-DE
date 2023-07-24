---
title: Neuerungen? Versionshinweise - Dienst für die automatische Formularkonvertierung
description: Erfahren Sie mehr über die neuesten Funktionen und Fehler, die für den Dienst für die automatische Formularkonvertierung behoben wurden
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: fccafbc9-28c1-4736-922c-24d675b25213
source-git-commit: e95b4ed35f27f920b26c05f3398529f825948f1f
workflow-type: ht
source-wordcount: '454'
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

## 24. Februar 2022 (AFC-2022.02.0) {#feb-2022}

* Es wurde die Möglichkeit hinzugefügt, [Abschnitte automatisch in Fragmente zu konvertieren](convert-existing-forms-to-adaptive-forms.md), um die Darstellungsgeschwindigkeit von konvertierten Formularen zu verbessern und das Laden großer Formulare im Editor für adaptive Formulare zu erleichtern.

## 29. August 2021 (AFC-2021.08.0) {#aug-2021}

* Eine Funktion wurde hinzugefügt, mit der PDF-Formulare auf Italienisch und Portugiesisch in adaptive Formulare konvertiert werden können.

## 29. Juli 2021 (AFC-2021.07.2) {#july-2021}

* Eine Funktion wurde hinzugefügt, mit der PDF-Formulare auf Deutsch, Französisch und Spanisch in adaptive Formulare konvertiert werden können.

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

Sie benötigen das Connector-Paket 1.1.38 oder höher, um die neuesten Funktionen und Verbesserungen der Version AFC-2020.03.1 verwenden zu können.

Wenn Sie bereits über eine Umgebung des Dienstes für die automatische Formularkonvertierung verfügen, installieren Sie zur Verwendung der neuesten Funktionen des Konvertierungsdiensts das neueste Service Pack, das neueste Add-On-Paket für AEM Forms und das neueste Connector-Paket in der angegebenen Reihenfolge. Genaue Anweisungen finden Sie unter [Dienst zur automatischen Formularkonvertierung konfigurieren](configure-service.md).
