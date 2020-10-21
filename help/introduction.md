---
title: Einführung
description: 'Schnellere Konvertierung von Druckformularen in adaptive Formulare '
translation-type: tm+mt
source-git-commit: c4f0d07b38cdb6aa162a0b61abe12fe9d1677a8c
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 92%

---


# Einführung {#introduction-to-automated-forms-conversion-service}

Der Dienst für die automatische Formularkonvertierung beschleunigt die Digitalisierung und Modernisierung der Datenerfassung durch die automatische Konvertierung von PDF-Formularen in adaptive Formulare. Der von Adobe Sensei unterstützte Dienst konvertiert Ihre PDF-Formulare automatisch in gerätefreundliche, responsive und HTML5-basierte adaptive Formulare. Der Dienst nutzt die vorhandenen Investitionen in PDF-Formulare und XFA und wendet während der Konvertierung auch entsprechende Validierungen, Stile und Layouts auf adaptive Formularfelder an. Der Dienst hilft bei Folgendem:

* Einsparung von manuellem Aufwand beim Konvertieren von Druckformularen in adaptive Formulare
* Anwendung von Mustern und entsprechender Validierungen während der Konvertierung 
* Generieren eines Datensatzdokuments während der Konvertierung
* Gruppieren Sie häufig vorkommender Felder in wiederverwendbaren Formularfragmente
* Aktivierung von Adobe Analytics während der Konvertierung

![Es ist einfach. Sie geben uns lediglich die Quellformulare und überlassen alles uns. Wir stellen Ihnen schöne adaptive Formulare bereit. Natürlich basteln Sie an der Ausgabe, bis Sie zufrieden sind. ](assets/pdf-to-adaptive-form-gitx50.gif)

## Einstieg {#onboarding}

Der Dienst steht AEM 6.4 Forms und AEM 6.5 Forms On-Premise-Kunden sowie Unternehmenskunden von Adobe Managed Service kostenlos zur Verfügung. Sie können sich an das Adobe Sales-Team oder Ihren Adobe-Vertreter wenden, um Zugriff auf den Service anzufordern.

Adobe ermöglicht den Zugriff für Ihre Organisation und stellt der in Ihrer Organisation als Administrator genannten Person die erforderlichen Berechtigungen zur Verfügung. Der Administrator kann den AEM Forms-Entwicklern (Benutzern) Ihrer Organisation Zugriff gewähren, um eine Verbindung zum Dienst herzustellen. Genaue Anweisungen finden Sie unter [Dienst zur automatischen Formularkonvertierung konfigurieren](configure-service.md).

## Unterstützte PDF-Formulare und Sprachen{#supported-languages-and-pdf-forms}

Der Dienst unterstützt nicht-interaktive PDF-Formulare, Formulare, die mit Adobe Acrobat erstellt wurden (AcroForms), und XFA-basierte Formulare, die mit AEM Forms oder Adobe LiveCycle erstellt wurden.

Der Dienst unterstützt auch Adobe Sign-aktivierte PDF forms. Wenn das Quell-PDF-Formular über Adobe Sign-Text-Tags verfügt, behält der Dienst alle Adobe Sign-bezogenen Informationen während der Konvertierung bei und verknüpft die in der Quell-PDF vorhandenen Signiererinformationen mit den entsprechenden Feldern des adaptiven Formulars. Die Funktion ist nur für AcroForms verfügbar.

Der Dienst kann nur englischsprachige Formulare in adaptive Formulare konvertieren. Sie können die generierten adaptiven Formulare mithilfe des [AEM Übersetzungs-Arbeitsablaufs ](https://helpx.adobe.com/de/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html) in andere Sprachen übersetzen.

## Konvertierungsarbeitsablauf  {#conversion-workflow}

Der Dienst für die automatische Formularkonvertierung läuft auf Adobe Cloud. Sie verbinden Ihre AEM-Instanz mit dem Dienst, laden Formulare in Ihre AEM-Instanz hoch und starten die Konvertierung. Der vollständige Konvertierungsprozess läuft ab wie folgt:

![Arbeitsablauf](assets/conversion-workflow.png)

### 1. Einrichten der Arbeitsumgebung {#set-up-the-environment}

Der Dienst für die automatische Formularkonvertierung läuft auf Adobe Cloud. [Konfigurieren Sie das Adobe I/O-Konto Ihrer Organisation und verbinden Sie Ihre lokale AEM-Instanz ](configure-service.md) mit dem Konvertierungsdienst, der in Adobe Cloud ausgeführt wird.

### 2. Konvertieren von PDF-Formularen in adaptive Formulare{#use-the-conversion-service}

Nachdem Sie Ihre AEM Forms-Umgebung konfiguriert haben, konvertieren Sie Ihre PDF-Formulare in adaptive Formulare, indem Sie [PDF-Formulare in Ihre AEM-Instanz hochladen](convert-existing-forms-to-adaptive-forms.md) und die [Konvertierung starten](convert-existing-forms-to-adaptive-forms.md#run-the-conversion). Beachten Sie vor dem Hochladen der Formulare Folgendes:

* Laden Sie nicht die gesicherten Formulare hoch. Der Dienst konvertiert keine kennwortgeschützten und verschlüsselten Formulare.
* Laden Sie keine gescannten, farbigen, nicht englischen und ausgefüllten Formulare hoch. Solche Formulare werden nicht unterstützt.
* Laden Sie keine PDF-Formulare mit Leerzeichen im Dateinamen hoch.
* Laden Sie keine [PDF-Portfolios](https://helpx.adobe.com/de/acrobat/using/overview-pdf-portfolios.html) hoch. Der Dienst konvertiert keine PDF-Portfolios in adaptive Formulare.
* Nehmen Sie die vorgeschlagenen Änderungen in PDF-Formularen vor, wie sie im Artikel [Best Practices und Überlegungen](styles-and-pattern-considerations-and-best-practices.md) beschrieben werden.
* Lesen Sie den Artikel [Bekannte Probleme](known-issues.md), um Fallstricke zu vermeiden.

### 3. Überprüfen der konvertierten Formulare {#review-converted-forms}

Reale Formulare können komplexe Anforderungen an die Datenerfassung in Bezug auf Feldlayout, Benennung oder implizite Vorschläge haben, die diet AI/ML-basierter Erkennungslogik möglicherweise nicht erfassen kann. Sobald die automatische Konvertierung abgeschlossen ist, können Sie im Editor [Überprüfen und Korrigieren](review-correct-ui-edited.md) das konvertierte Formular überprüfen, erforderliche Aktualisierungen vornehmen und eine verbesserte Ausgabe generieren, die dem gewünschten Ergebnis näher kommt. Nachdem Sie die erforderlichen Änderungen vorgenommen haben, senden Sie das Formular erneut zur Konvertierung.

Die für die automatische Konvertierung benötigte Zeit hängt von einer Vielzahl von Faktoren ab, z. B. der Größe und Komplexität des Eingabeformulars und der Beanspruchung der Verarbeitungswarteschlange des Dienstes. Der Benutzer wird regelmäßig über die Statusanzeige im Ordner/in der Datei über den Fortschritt informiert. Nach Abschluss der Konvertierung wird auch eine E-Mail-Benachrichtigung an die konfigurierte E-Mail-Adresse gesendet.
