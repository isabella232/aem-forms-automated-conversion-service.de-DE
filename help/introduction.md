---
title: Einführung
description: 'Beschleunigung der Konvertierung von Druckformularen in adaptive Formulare '
translation-type: tm+mt
source-git-commit: ef5789dabccc65dcf988b9424b435aa036017691

---


# Einführung {#introduction-to-automated-forms-conversion-service}

Der Dienst &quot;Automatisierte Formularkonvertierung&quot;beschleunigt die Digitalisierung und Modernisierung der Datenerfassung durch automatisierte Konvertierung von PDF-Formularen in adaptive Formulare. Der Dienst mit Adobe Sensei konvertiert Ihre PDF-Formulare automatisch in gerätefreundliche, reaktionsfähige und HTML5-basierte adaptive Formulare. Bei der Nutzung der vorhandenen Investitionen in PDF-Formulare und XFA wendet der Dienst während der Konvertierung auch geeignete Überprüfungen, Stile und Layouts auf adaptive Formularfelder an. Der Dienst unterstützt:

* Sparen Sie den manuellen Aufwand für die Konvertierung von Druckformularen in adaptive Formulare
* Wendet Muster und geeignete Überprüfungen während der Konvertierung an
* Dokument aus Datensatz während der Konvertierung erstellen
* Gruppieren häufig vorkommender Felder in wiederverwendbaren Formularfragmenten
* Aktiviert Adobe Analytics während der Konvertierung

![Es ist einfach. Sie geben uns einfach die Quellformulare und überlassen uns alles. Wir stellen Ihnen schöne adaptive Formulare zur Verfügung. Natürlich werden Sie mit der Ausgabe zu Ihrer Zufriedenheit. ](assets/pdf-to-adaptive-form-gitx50.gif)

## Einstieg {#onboarding}

Der Dienst steht Kunden von AEM 6.5 Forms On-Premise-Terminologiekunden und Adobe Managed Service-Unternehmenskunden kostenlos zur Verfügung. Sie können sich an das Adobe Sales Team oder Ihren Adobe-Kundenbetreuer wenden, um Zugriff auf den Dienst anzufordern.

Adobe ermöglicht den Zugriff auf Ihr Unternehmen und stellt die erforderlichen Berechtigungen für die Person bereit, die als Administrator in Ihrem Unternehmen benannt wurde. Der Administrator kann Ihren AEM Forms-Entwicklern (Benutzern) Ihres Unternehmens Zugriff auf die Verbindung zum Dienst gewähren. Weitere Informationen finden Sie unter [Konfigurieren des Dienstes](configure-service.md) für die automatisierte Formularkonvertierung.

## Unterstützte PDF-Formulare und -Sprachen {#supported-languages-and-pdf-forms}

Der Dienst unterstützt nicht interaktive PDF-Formulare, mit Adobe Acrobat erstellte Formulare, AcroForms, und XFA-basierte Formulare, die mit AEM Forms oder Adobe LiveCycle erstellt wurden.

Der Dienst kann nur englischsprachige Formulare in adaptive Formulare konvertieren. Sie können die erstellten adaptiven Formulare mit dem [AEM-Übersetzungs-Workflow](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)in eine andere Sprache übersetzen.

## Konvertierungsarbeitsablauf {#conversion-workflow}

Der Dienst &quot;Automatisierte Formularkonvertierung&quot;wird auf Adobe Cloud ausgeführt. Sie verbinden Ihre AEM-Instanz mit dem Dienst, laden Formulare in Ihre AEM-Instanz hoch und starten die Konvertierung. Der vollständige Konvertierungsprozess ist wie folgt:

![Workflow](assets/conversion-workflow.png)

### 1.Einrichten der Umgebung {#set-up-the-environment}

Der Dienst &quot;Automatisierte Formularkonvertierung&quot;wird auf Adobe Cloud ausgeführt. [Konfigurieren Sie das Adobe-E/A-Konto Ihres Unternehmens und verbinden Sie Ihre lokale AEM-Instanz](configure-service.md) mit dem Konvertierungsdienst, der in der Adobe Cloud ausgeführt wird.

### 2.Konvertieren von PDF-Formularen in adaptive Formulare {#use-the-conversion-service}

Nachdem Sie Ihre AEM Forms-Umgebung konfiguriert haben, können Sie Ihre PDF-Formulare in adaptive Formulare konvertieren, PDF-Formulare[ in Ihre AEM-Instanz ](convert-existing-forms-to-adaptive-forms.md)hochladen und die Konvertierung[](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)starten. Beachten Sie vor dem Hochladen der Formulare Folgendes:

* Laden Sie die geschützten Formulare nicht hoch. Der Dienst konvertiert keine kennwortgeschützten und verschlüsselten Formulare.
* Laden Sie keine gescannten, farbigen, nicht englischsprachigen und ausgefüllten Formulare hoch. Solche Formulare werden nicht unterstützt.
* Laden Sie keine PDF-Formulare mit Leerzeichen im Dateinamen hoch.
* Laden Sie keine [PDF-Portfolios](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html)hoch. Der Dienst konvertiert kein PDF-Portfolio in adaptive Formulare.
* Nehmen Sie die vorgeschlagenen Änderungen in PDF-Formularen vor, die im Artikel [Empfohlene Vorgehensweisen und Überlegungen](styles-and-pattern-considerations-and-best-practices.md) beschrieben werden.
* Lesen Sie den Artikel [Bekannte Probleme](known-issues.md) , um Fallstricke zu vermeiden.

### 3. Konvertierte Formulare überprüfen {#review-converted-forms}

Real-world-Formulare können komplexe Anforderungen an die Datenerfassung in Bezug auf Feldlayout, Benennung oder implizite Vorschläge haben, die möglicherweise nicht mit AI/ML-basierter Erkennungslogik erfasst werden. Nachdem die automatisierte Konvertierung abgeschlossen ist, können Sie mit dem Editor [](review-correct-ui-edited.md) &quot;Überprüfen&quot;und &quot;Korrigieren&quot;das konvertierte Formular überprüfen und die erforderlichen Aktualisierungen vornehmen und eine erweiterte Ausgabe erstellen, die dem gewünschten Erlebnis näher kommt. Nachdem Sie die erforderlichen Änderungen vorgenommen haben, senden Sie das Formular erneut für die Konvertierung.

Die für die automatisierte Konvertierung benötigte Zeit hängt von verschiedenen Faktoren ab, wie z.B. der Größe des Eingabefelds, der Komplexität des Formulars und dem Darlehen in der Verarbeitungswarteschlange des Dienstes. Der Benutzer wird regelmäßig über die Statusanzeige in Ordner/Datei über den Fortschritt informiert. Nach Abschluss der Konvertierung wird eine E-Mail-Benachrichtigung auch an die konfigurierte E-Mail-Adresse gesendet.
