---
title: Häufig gestellte Fragen
seo-title: Häufig gestellte Fragen
description: Häufige Abfragen oder häufig gestellte Fragen
seo-description: Häufig gestellte Fragen zum automatisierten Forms-Konvertierungsdienst
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
translation-type: tm+mt
source-git-commit: 1e22587a832ca8d09f33141a9ba4e4b1748e0312

---


# Häufig gestellte Fragen{#frequently-asked-questions}

1. **Welche Version von AEM Forms unterstützt der Automatisierte Forms-Konvertierungsdienst?**
   <p>Der Automatisierte Forms-Konvertierungsdienst unterstützt AEM 6.5 Forms. Es funktioniert sowohl mit AEM Forms on OSGi als auch mit AEM Forms on JEE. Sie benötigen das neueste Add-On-Paket für AEM Forms über der AEM-Autoreninstanz, um den Dienst zu verwenden. Detaillierte Anweisungen finden Sie unter <a href="configure-service.md">Konfigurieren des Dienstes "Automatisierte Formularkonvertierung</a> ".</p> 
    <br>

1. **Kann der Dienst vor Ort installiert werden?**
   <p>Adobe schult regelmäßig AI- und ML-Algorithmen des Dienstes "Automatisierte Formularkonvertierung"mit neuen Datensätzen, um die Konvertierungsgenauigkeit zu verbessern. Die aktualisierten Algorithmen werden in regelmäßigen Abständen für den Konvertierungsdienst bereitgestellt, der in Adobe Cloud ausgeführt wird. Alle Kunden des Dienstes profitieren von den aktualisierten Algorithmen. Die zentrale Bereitstellung mit Cloud-Hosting eignet sich daher am besten für den automatisierten Forms-Konvertierungsdienst, um ständig zu lernen und Verbesserungen für alle Kunden bereitzustellen.</p> 
    <p>Der Dienst konvertiert leere Formulare in adaptive Formulare. Der Dienst unterstützt keine ausgefüllten Formulare und das Extrahieren von Daten aus ausgefüllten Formularen. Entfernen Sie Daten aus ausgefüllten Formularen und entfernen oder weisen Sie proprietäre Informationen aus den Formularen auf, bevor Sie die Formulare zur Konvertierung an den Dienst senden</p> <br>

1. **Unterstützt der Dienst alle Formate von PDF-Formularen? Welche Sprachen werden unterstützt?**
   <p>Der Dienst kann nicht interaktive PDF-Formulare, XFA-basierte XDP- und PDF-Formulare und AcroForms in adaptive Formulare konvertieren. Der Dienst unterstützt keine gescannten oder ausgefüllten Formulare. Weitere Einschränkungen finden Sie im Artikel zu <a href="known-issues.md">bekannten Problemen</a> .<br /> </p> 
    <p>Regelmäßig wird Unterstützung für andere Quelltypen hinzugefügt. Behalten Sie den Abschnitt <a href="introduction.md">Unterstützte PDF-Formulare</a> in Ihrer Überwachungsliste bei, um regelmäßige Aktualisierungen zu neuen Funktionen zu erhalten.</p>

   Der Dienst kann nur englischsprachige Formulare in adaptive Formulare konvertieren. Sie können die erstellten adaptiven Formulare mit dem [AEM-Übersetzungs-Workflow in eine andere Sprache übersetzen.](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **Kann der Dienst anstelle eines adaptiven Formulars eine XDP erstellen?**
   <p>Der Dienst erzeugt keine XDP-Ausgabe. Wir fügen regelmäßig Funktionen und Dienste hinzu. Behalten Sie die <a href="introduction.md">unterstützten Sprachen und PDF-Formulare</a> in Ihrer Überwachungsliste bei, um regelmäßige Aktualisierungen zu neuen Funktionen zu erhalten.</p> <br>

1. **Was ist der Typ des generierten Schemas?**
   <p>Mit dem Dienst können Sie Folgendes generieren: </p>

   * ein an ein JSON-Schema gebundenes adaptives Formular und
   * ein adaptives Formular, das an kein Schema gebunden ist <br><br>

1. **Kann der Dienst ein Microsoft Word-Formular in adaptive Formulare konvertieren?**
   <p>Nein, der Dienst konvertiert kein Microsoft Word-Formular in ein adaptives Formular. Sie können Microsoft Word-Formulare als PDF-Formular speichern und das PDF-Formular in ein adaptives Formular konvertieren. Der vollständige Prozess ist </p> <br>

   1. Verwenden Sie Adobe Acrobat, um Word-Dokumente in nicht interaktive PDF-Dokumente zu [konvertieren](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Verwenden Sie Adobe Acrobat, um die erstellten PDF-Formulare in ausfüllbare PDF-Formulare zu [konvertieren](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. Mit Adobe Acrobat können Sie Formularfelder manuell aktualisieren und reparieren.
   1. Speichern Sie das PDF-Formular. Jetzt können Sie das Formular mit dem Konvertierungsdienst verwenden, um ein adaptives Formular zu generieren. Sie können das Formular auch als Datensatzdokument-Vorlage verwenden.


1. **Kann der Dienst gescannte Papierformulare und farbige Formulare in adaptive Formulare konvertieren?**
   <p>Der Dienst kann PDF-Formulare in adaptive Formulare konvertieren. Der Dienst unterstützt keine gescannten oder ausgefüllten Formulare. Weitere Einschränkungen finden Sie im Artikel zu <a href="known-issues.md">bekannten Problemen</a> .</p> <br>

1. **Kann der Dienst ein gescanntes Formular oder nur ein Bild eines Formulars in ein adaptives Formular konvertieren?**
   <p>Der Dienst unterstützt nicht die Konvertierung gescannter Formulare oder eines Formularbilds in ein vordefiniertes adaptives Formular. Sie verwenden Adobe Acrobat jedoch, um das Bild eines Formulars in ein PDF-Formular zu konvertieren. Verwenden Sie dann den Dienst, um das PDF-Formular in ein adaptives Formular zu konvertieren. Verwenden Sie immer ein hochwertiges Bild des Formulars zur Konvertierung in Acrobat. Sie verbessert die Qualität der Konvertierung.</p> <br>

1. **Einige XDP-basierte Formulare verwenden Formularfragmente. Wo sollten diese Formularfragmente hochgeladen werden?**
   <p class="MsoNormal">Laden Sie Formularfragmente in den Konvertierungsordner hoch und behalten Sie die ursprüngliche Ordnerstruktur bei. Auf diese Weise können Sie relative Pfade beibehalten, die in XDP-basierten Formularen und Formularfragmenten verwendet werden.</p> <br>

1. **Unterstützt der Dienst schemabindete XDP-Formulare? Wenn ich eine XDP an ein Schema gebunden habe, muss ich dann Schema in XDP einbetten?**
   <p>Ja, der Dienst unterstützt schemagebundene XDP-Formulare und erfordert, dass das Schema in das Quell-XDP-Formular eingebettet wird. Wenn Sie ein schemagebundenes XDP-Formular konvertieren, generiert der Dienst ein JSON-Schema. Das JSON-Schema ähnelt strukturell dem XSD-Schema der XDP-Quellformulare.</p> <br>

1. **Der Dienst konnte keine Formulare konvertieren. Aus welchem Grund und wie lässt sich das Problem lösen?**
Die häufigsten Gründe für das Fehlschlagen der Konvertierung sind:</p>
   * Für die Konvertierung werden geschützte PDF-Formulare bereitgestellt. Verwenden Sie keine kennwortgeschützten oder geschützten PDF-Formulare zur Konvertierung.
   * Die Internetverbindung wird unterbrochen. Stellen Sie sicher, dass Sie während der Konvertierung mit dem Internet verbunden sind.
   * Die Quell-PDF enthält ein Bild des Formulars anstelle des eigentlichen Formulars.
   * Dienst ist falsch konfiguriert, Dienst-URL nicht bereitgestellt oder die Dienst-URL ist nicht korrekt. Überprüfen Sie die [Dienstkonfiguration](configure-service.md#configure-the-cloud-service) unter **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * Die IMS-Konfiguration ist nicht richtig konfiguriert. Führen Sie eine Überprüfung der IMS-Konfiguration durch, um sicherzustellen, dass sie ordnungsgemäß funktioniert. So prüfen Sie, ob die IMS-Konfiguration korrekt ist:
      1. Wechseln zu `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Wählen Sie die Konfiguration aus. Klicken Sie auf die **[!UICONTROL Check Health]** Kopfzeile und dann auf **[!UICONTROL Check]**. Bei Erfolg erhalten Sie eine **[!UICONTROL Token retrieved successfully!]** Nachricht. <br> <br>

1. **Hat die Verwendung von benutzerdefinierten Schriftarten Auswirkungen auf die Konversion?**
   <p>Wenn ein nicht interaktives PDF-Formular in ein adaptives Formular konvertiert wird, um die Konvertierungsqualität zu verbessern, werden die Schriftarten in das PDF-Formular eingebettet. Die Unterstützung für das Einbetten von Schriftarten ist auf nicht interaktive PDF-Formulare beschränkt. Zur Optimierung der Konvertierung von AcroForm- und XFA-basierten PDF-Formularen werden Ersatzschriftarten verwendet.</p> 
    <p>Nur Formulare, die im Ordner für benutzerdefinierte Schriftarten verfügbar sind, die im Feld "Verzeichnis<strong> für </strong>Kundenschriftarten"der Konfiguration des <strong> CQ-DAM-Handler-Gibson Font Manager-Dienstes</strong> aufgeführt sind, sind in nicht interaktive PDF-Formulare eingebettet.</p> 
    <p> </p> <br>

1. **Identifiziert und verwendet der Dienst Schriftarten der Quell-PDF in Ausgabe-adaptiven Formularen?**
   <p>Stil und Layout eines interaktiven HTML-Formulars unterscheiden sich im Allgemeinen von einem PDF- oder einem papierbasierten Formular. Um ein konsistentes Layout und eine einheitliche Formatierung in allen Unternehmen zu unterstützen, verwenden adaptive Formulare <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">Designs zum Formatieren eines Formulars</a>. Der Konvertierungsdienst verwendet die Schriftarten und Schriftstile, die im Design angegeben wurden, das während der Konvertierung angewendet wurde. Sie können Schriftarten und Schriftschnitte des Designs ändern, um den Komponenten eines adaptiven Formulars ein unverwechselbares Erscheinungsbild zu verleihen.</p> <br>

1. **Extrahiert der Dienst automatisch JavaScript aus XDP-basierten Formularen und wendet er es auf entsprechende adaptive Formulare an?**
   <p>Der Dienst konvertiert Skripten von XFA-basierten Formularen oder Acro Forms nicht automatisch in entsprechende adaptive Formularregeln. Sie (Formularverfasser) können mit dem <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">Regeleditor</a> Interaktivität zu einem adaptiven Formular hinzufügen.</p> <br>

1. **Einige Formularobjekte werden nicht korrekt in Komponenten für adaptive Formulare konvertiert. How to resolve the issue?**
   <p>Der Dienst für die automatisierte Formularkonvertierung wird für eine große Anzahl von Formularen geschult. AI/ML-basierte Anwendungen sind jedoch durch ihre Schulungsdaten und -muster eingeschränkt. Es können mehrere Feldtypen, Layouts, Muster und Kontext vorhanden sein, die für die menschliche Wahrnehmung erkennbar sind, die aber für die automatisierte Erkennung schwierig sind. Der Dienst kann diese Objekte möglicherweise nicht oder nicht richtig erkennen. Sie können den Editor <a href="review-correct-ui-edited.md" target="_blank">"Review"und "Korrekt</a> "verwenden, um die erforderlichen Änderungen am vertrauten papierbasierten Layout des Eingabefelds vorzunehmen.</p> <br/>

1. **Einige Korrekturen werden formularübergreifend wiederholt. Kann der Dienst alle derartigen Instanzen in zukünftigen Konvertierungen identifizieren und beheben?**

   Der Dienst führt regelmäßig Schulungen zu Ihren Formularen und Mustern durch. Es lernt täglich neue Muster. Es ist noch nicht möglich, Korrekturen automatisch anzuwenden, die in allen Formularen wiederholt werden. Achten Sie auf Vorabversionsformulare, um eine solche Funktion bereitzustellen. <br/><br/>

   Sie können das Metadatenmodell verwenden, um die Formularobjekte der Komponente für adaptive Formulare Ihrer Wahl zuzuordnen und Überprüfungen, Regeln, Datenmuster, Hilfetext und Barrierefreiheitseigenschaften für die Komponenten vorkonfigurieren. Alle angegebenen Eigenschaften werden während der Konvertierung angewendet. Mit dem Metamodell können Sie allgemeine Eigenschaften auf Felder anwenden. Dadurch können Sie einige wiederholte Probleme in allen Formularen reduzieren.<br/><br/>

1. **Welche Optionen gibt es für Formulare mit sensiblen Daten wie personenbezogene Daten (PII)?**
Der Dienst unterstützt nur leere oder nicht ausgefüllte Formulare. Laden Sie keine ausgefüllten Formulare oder Formulare mit personenbezogenen Daten (PII) hoch. Entfernen Sie außerdem vorausgefüllte Daten und White-Label-PII, vertrauliche und proprietäre Informationen in Quellformularen. <br/>

1. **Wo sollten Kopf- und Fußzeilen platziert werden?**
   <p>Platzieren Sie Kopf- und Fußzeile in einer Vorlage für adaptive Formulare. Wenn das PDF-Quellformular Kopf- und Fußzeile enthält, erkennt und ersetzt der Dienst die erkannte Kopf- und Fußzeile während der Konvertierung in der Vorlage für adaptive Formulare. Wenn eine zusätzliche Kopf- oder Fußzeile im adaptiven Formular enthalten ist, können Sie diese Kopf- oder Fußzeile mit dem Editor <a href="review-correct-ui-edited.md">Überprüfen und Korrigieren</a> beheben oder entfernen.</p> <br />

1. **Wie viel Zeit spart der Dienst im Vergleich zum manuellen Planen, Erstellen von Assets (Designs, Vorlagen), Erstellen und Veröffentlichen eines adaptiven Formulars?**
   <p>Die Zeitdauer hängt von der Größe und Komplexität der Eingabeformulare und der Anzahl der Anforderungen ab. Der Dienst beabsichtigt, die Zeit bis zur Wertschöpfung erheblich zu reduzieren, indem PDF-Formulare in adaptive Formulare umgewandelt werden, was im Vergleich zum manuellen Konvertieren von Formularen viel schneller ist. </p> <br />

1. **Was muss ich tun, wenn ich einen Fehler in Zusammenhang mit RSA-Bibliotheken bekomme?** Die Fehlermeldung ähnelt der folgenden: <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` Der <br>vorgenannte Fehler tritt auf, wenn die Boot-Delegierung nicht für RSA/BouncyCastle-Bibliotheken konfiguriert ist. Führen Sie die folgenden Schritte aus, um das Problem zu beheben:
   <p> </p>

   1. Halten Sie die AEM-Instanz an. Navigate to the `[AEM installation directory]\crx-quickstart\conf\` folder. Öffnen Sie die Datei &quot;sling.properties&quot;zur Bearbeitung. Wenn Sie eine AEM-Instanz `[AEM installation directory]\crx-quickstart\bin\start.bat` starten, bearbeiten Sie die Datei sling.properties unter `[AEM_root]\crx-quickstart\`.
   1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Speichern und schließen Sie die Datei. <br/>
   1. Starten Sie die AEM-Instanz.<br/>
   <br/>

1. **Wie lässt sich die Darstellung des adaptiven Formulartextes automatisch ändern?**
   <p>Sie können adaptive Formulare aus dem Design- oder Stileditor verwenden, um die Darstellung eines Felds des adaptiven Formulars zu ändern. Sie können beispielsweise den Design-Editor öffnen und den Wert der Eigenschaft "Groß-/Kleinschreibung"für den gesamten Text des Formulars auf "Großbuchstaben", "Kleinbuchstaben"oder "Groß-/Kleinschreibung"setzen. Sie können auch die Option "CSS-Überschreibung"im Design-Editor verwenden, um verschiedene Stiltypen zu erstellen.</p>