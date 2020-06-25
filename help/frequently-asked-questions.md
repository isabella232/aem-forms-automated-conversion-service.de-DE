---
title: Häufig gestellte Fragen
seo-title: Häufig gestellte Fragen
description: Häufige Fragen oder häufig gestellte Fragen
seo-description: häufig gestellte Fragen für den Dienst für die automatische Formularkonvertierung
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
translation-type: tm+mt
source-git-commit: 3b3bb98352e23544d32c39f0bfb5f0d9b7ae99cf
workflow-type: tm+mt
source-wordcount: '1722'
ht-degree: 99%

---


# Häufig gestellte Fragen{#frequently-asked-questions}

1. **Welche Version von AEM Forms unterstützt der Dienst für die automatische Formularkonvertierung?**
   <p>Der Dienst für die automatische Formularkonvertierung unterstützt AEM 6.4 Forms und AEM 6.5 Forms. Es funktioniert sowohl mit AEM-Formularen unter OSGi als auch mit AEM-Formularen unter JEE. Sie benötigen das neueste AEM Forms-Add-On-Paket zusätzlich zur AEM-Autoreninstanz, um den Dienst nutzen zu können. Genaue Anweisungen finden Sie unter <a href="configure-service.md">Dienst zur automatischen Formularkonvertierung konfigurieren</a>.</p> 
    <br>

1. **Kann der Dienst vor Ort installiert werden?**
   <p>Adobe schult regelmäßig AI- und ML-Algorithmen des Dienstes für die automatische Formularkonvertierung mit neuen Daten, um die Konvertierungsgenauigkeit zu verbessern. Die aktualisierten Algorithmen werden in regelmäßigen Abständen für den in Adobe Cloud ausgeführten Konvertierungsdienst bereitgestellt. Alle Kunden des Dienstes profitieren von den aktualisierten Algorithmen. Die in der Cloud gehostete zentrale Bereitstellung eignet sich daher am besten für den Dienst für die automatische Formularkonvertierung, da diese auf diese Weise kontinuierlich lernen kann und Verbesserungen für alle Kunden möglich werden.</p> 
    <p>Der Dienst konvertiert leere Formulare in adaptive Formulare. Der Dienst unterstützt keine ausgefüllten Formulare und das Extrahieren von Daten aus ausgefüllten Formularen. Entfernen Sie Daten aus ausgefüllten Formularen und entfernen oder schützen Sie proprietäre Informationen aus den Formularen, bevor Sie die Formulare zur Konvertierung an den Dienst senden</p> <br>

1. **Unterstützt der Dienst alle Formate von PDF-Formularen? Werden alle Sprachen unterstützt?**
   <p>Der Dienst kann nicht-interaktive PDF-Formulare, XFA-basierte XDP- und PDF-Formulare sowie AcroForms in adaptive Formulare konvertieren. Der Dienst unterstützt keine gescannten oder ausgefüllten Formulare. Weitere Einschränkungen finden Sie im Artikel <a href="known-issues.md">Bekannte Probleme</a>.<br /> </p> 
    <p>Wir fügen regelmäßig Unterstützung für andere Quelltypen hinzu. Behalten Sie den Abschnitt <a href="introduction.md">unterstützte PDF-Formulare</a> auf Ihrer Beobachtungsliste, um regelmäßig über neu hinzugefügte Funktionen und Features informiert zu werden.</p>

   Der Dienst kann nur englischsprachige Formulare in adaptive Formulare konvertieren. Sie können die generierten adaptiven Formulare mithilfe des [AEM Übersetzungs-Arbeitsablaufs](https://helpx.adobe.com/de/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html) in andere Sprachen übersetzen.</br> </br>

1. **Kann der Dienst ein XDP anstelle eines adaptiven Formulars erstellen?**
   <p>Der Dienst erzeugt keine XDP-Ausgabe. Wir fügen regelmäßig Funktionen zum Dienst hinzu. Behalten Sie den Abschnitt <a href="introduction.md">unterstützte PDF-Formulare</a> auf Ihrer Beobachtungsliste, um regelmäßig über neu hinzugefügte Funktionen und Features informiert zu werden.</p> <br>

1. **Was ist der Typ des generierten Schemas?**
   <p>Mit dem Dienst können Sie Folgendes generieren: </p>

   * ein adaptives Formular, das an ein JSON-Schema gebunden ist und
   * ein adaptives Formular, das an kein Schema gebunden ist<br><br>

1. **Kann der Dienst ein Microsoft Word-Formular in adaptive Formulare konvertieren?**
   <p>Nein, der Dienst konvertiert Microsoft Word-Formulare nicht in adaptive Formulare. Sie können ein Microsoft Word-Formular in ein PDF-Formular speichern und das PDF-Formular in ein adaptives Formular konvertieren. Der gesamte Prozess läuft wie folgt ab: </p> <br>

   1. Konvertieren Sie mithilfe von Adobe Acrobat [das Word-Dokument in eine nicht-interaktive PDF](https://helpx.adobe.com/de/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Konvertieren Sie in Adobe Acrobat [die so erstellten PDF-Formulare in ausfüllbare PDF-Formulare](https://helpx.adobe.com/de/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. Korrigieren und aktualisieren Sie in Adobe Acrobat manuell die Formularfelder.
   1. Speichern Sie das PDF-Formular. Jetzt können Sie das Formular mit dem Konvertierungsdienst verwenden, um ein adaptives Formular zu generieren. Sie können das Formular auch als Datensatzdokument-Vorlage verwenden.


1. **Kann der Dienst gescannte Papierformulare und farbige in adaptive Formulare konvertieren?**
   <p>Der Dienst kann PDF-Formulare in adaptive Formulare konvertieren. Der Dienst unterstützt keine gescannten oder ausgefüllten Formulare. Weitere Einschränkungen finden Sie im Artikel <a href="known-issues.md">Bekannte Probleme</a>.</p> <br>

1. **Kann der Dienst ein gescanntes Formular oder nur ein Bild eines Formulars in ein adaptives Formular konvertieren?**
   <p>Der Dienst unterstützt nicht standardmäßig das Konvertieren gescannter Formulare oder eines Bilds eines Formulars in ein adaptives Formular. Sie können jedoch in Adobe Acrobat das Bild eines Formulars in ein PDF-Formular konvertieren. Verwenden Sie dann den Dienst, um das PDF-Formular in ein adaptives Formular zu konvertieren. Verwenden Sie für die Konvertierung in Acrobat immer ein qualitativ hochwertiges Bild des Formulars. Es verbessert die Qualität der Konvertierung.</p> <br>

1. **Einige XDP-basierte Formulare verwenden Formularfragmente. Wo sollen diese Formularfragmente hochgeladen werden?**
   <p class="MsoNormal">Laden Sie Formularfragmente in den Konvertierungsordner hoch und behalten Sie die ursprüngliche Ordnerstruktur bei. Auf diese Weise können Sie relative Pfade beibehalten, die in XDP-basierten Formularen und Formularfragmenten verwendet werden.</p> <br>

1. **Unterstützt der Dienst schemagebundene XDP-Formulare? Wenn ich ein XDP an ein Schema gebunden habe, muss ich das Schema in XDP einbetten?**
   <p>Ja, der Dienst unterstützt schemagebundene XDP-Formulare und erfordert, dass das Schema in das XDP-Quellformular eingebettet ist. Wenn Sie ein schemagebundenes XDP-Formular konvertieren, generiert der Dienst ein JSON-Schema. Das JSON-Schema ähnelt strukturell dem XSD-Schema von XDP-Quellformularen.</p> <br>

1. **Der Dienst konnte keine Formulare konvertieren. Was ist der Grund und wie kann das Problem behoben werden?**
Die häufigsten Gründe für das Fehlschlagen der Konvertierung sind:</p>
   * Für die Konvertierung werden gesicherte PDF-Formulare bereitgestellt. Verwenden Sie für die Konvertierung keine kennwortgeschützten oder gesicherten PDF-Formulare.
   * Die Internetverbindung ist unterbrochen. Stellen Sie sicher, dass Sie während der Konvertierung mit dem Internet verbunden sind.
   * Die Quell-PDF enthält ein Bild des Formulars anstelle des eigentlichen Formulars.
   * Der Dienst ist falsch konfiguriert, die Dienst-URL wird nicht bereitgestellt oder die bereitgestellte Dienst-URL ist falsch. Überprüfen Sie die [Dienstkonfiguration](configure-service.md#configure-the-cloud-service) unter **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Dienste]** > **[!UICONTROL Konfiguration der automatischen Formularkonvertierung]**.
   * Die IMS-Konfiguration ist nicht richtig konfiguriert. Führen Sie eine Integritätsprüfung der IMS-Konfiguration durch, um sicherzustellen, dass sie ordnungsgemäß funktioniert. So überprüfen Sie, ob die IMS-Konfiguration korrekt ist oder nicht:
      1. Wechseln zu `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Wählen Sie die Konfiguration aus. Klicken Sie in der Kopfzeile auf **[!UICONTROL Systemdiagnose]** und dann auf **[!UICONTROL Prüfen]**. Bei Erfolg wird **[!UICONTROL Token erfolgreich abgerufen!]** angezeigt. <br> <br>

1. **Beeinflusst die Verwendung benutzerdefinierter Schriftarten die Konvertierung?**
   <p>Wenn ein nicht-interaktives PDF-Formular in ein adaptives Formular konvertiert wird, werden die Schriftarten in das PDF-Formular eingebettet, um die Konvertierungsqualität zu verbessern. Die Unterstützung für das Einbetten von Schriftarten ist auf nicht-interaktive PDF-Formulare beschränkt. Um die Konvertierung von AcroForm- und XFA-basierten PDF-Formularen zu optimieren, werden Fallback-Schriftarten verwendet.</p> 
    <p>Nur Formulare, die im Verzeichnis der benutzerdefinierten Schriften im Feld <strong>Verzeichnis für Kundenschriftarten</strong> der Konfiguration <strong> CQ-DAM Handler Gibson Font Manager Service </strong> verfügbar sind, werden in nicht-interaktive PDF-Formulare eingebettet.</p> 
    <p> </p> <br>

1. **Identifiziert und verwendet der Dienst Schriftarten von Quell-PDF in den ausgegebenen adaptiven Formularen?**
   <p>Stil und Layout eines Responsive-HTML-Formulars unterscheiden sich grundsätzlich von einem PDF- oder papierbasierten Formular. Um ein einheitliches Layout und Styling in allen Organisationen zu unterstützen, verwenden adaptive Formulare <a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/using/themes.html">Designs zum Gestalten eines Formulars</a>). Der Konvertierungsdienst verwendet die Schriftarten und Schriftstile, die im während der Konvertierung angewendeten Design angegeben sind. Sie können Schriftarten und Schriftstile des Designs ändern, um den Komponenten eines adaptiven Formulars ein eindeutiges Erscheinungsbild zu verleihen.</p> <br>

1. **Extrahiert der Dienst automatisch JavaScript aus XDP-basierten Formularen und wendet er es dann auf entsprechende adaptive Formulare an?**
   <p>Der Dienst konvertiert Skripte von XFA-basierten Formularen oder Acro Forms nicht automatisch in entsprechende adaptive Formularregeln. Sie (Formular-Autoren) können den <a href="https://helpx.adobe.com/de/experience-manager/6-5/forms/using/rule-editor.html">Regeleditor</a> verwenden, um Interaktivität zu einem adaptiven Formular hinzuzufügen.</p> <br>

1. **Einige Formularobjekte werden nicht korrekt in adaptive Formularkomponenten konvertiert. Wie kann das Problem gelöst werden?**
   <p>Der Dienst zur automatischen Formularkonvertierung wird für eine Vielzahl von Formularen geschult. AI/ML-basierte Anwendungen sind jedoch durch ihre Trainingsdaten und -muster begrenzt. Es kann mehrere Feldtypen, Layouts, Muster und Kontexte geben, die für die menschliche Wahrnehmung erkennbar sind, für die eine automatische Erkennung jedoch schwierig ist. Der Dienst kann solche Objekte möglicherweise nicht identifizieren oder falsch erkennen. Sie können den Editor <a href="review-correct-ui-edited.md" target="_blank">Überprüfen und Korrigieren</a> verwenden, um die erforderlichen Änderungen im vertrauten papierformularbasierten Layout des Eingabeformulars vorzunehmen.</p> <br/>

1. **Einige Korrekturen werden formularübergreifend wiederholt. Kann der Dienst alle derartigen Instanzen in zukünftigen Konvertierungen identifizieren und beheben?**

   Der Dienst lernt laufend weiterhin an Ihren Formularen und Mustern. Er lernt täglich neue Muster. Die automatische Anwendung von Korrekturen, die in den Formularen wiederholt werden, ist noch nicht möglich. Behalten Sie Vorabversionsformulare im Auge, damit Sie es erfahren, wenn eine solche Funktion eingeführt wird. <br/><br/>

   Mithilfe des Metamodells können Sie die Formularobjekte Komponenten Ihrer Wahl in einem adaptiven Formular zuordnen und Validierungen, Regeln, Datenmuster, Hilfetexte und Eingabehilfen für die Komponenten vorkonfigurieren. Alle angegebenen Eigenschaften werden während der Konvertierung angewendet. Sie können das Metamodell verwenden, um allgemeine Eigenschaften auf Felder anzuwenden. Es kann Ihnen helfen, einige sich wiederholende Probleme in verschiedenen Formularen zu reduzieren.<br/><br/>

1. **Welche Optionen gibt es für Formulare mit sensiblen Daten wie personenbezogenen Daten?**
Der Dienst unterstützt nur leere oder nicht ausgefüllte Formulare. Laden Sie keine ausgefüllten Formulare oder Formulare mit personenbezogenen Daten hoch. Entfernen Sie außerdem vorausgefüllte Daten, persönliche identifizierbare Informationen (PII), vertrauliche und proprietäre Informationen in Quellformularen. <br/>

1. <br/>**
   </p>

1. 
   </p>

1.    **Was tun, wenn ein Fehler in Verbindung mit RSA-Bibliotheken auftritt ? Die Fehlermeldung ähnelt der unten genannten Meldung:** <br/>

Der oben genannte Fehler tritt auf, wenn die Startdelegierung nicht für RSA/BouncyCastle-Bibliotheken konfiguriert ist. Führen Sie zur Behebung dieses Problems folgende Schritte durch:
   </p>

   1. 
   1. Halten Sie die AEM-Instanz an. Navigieren Sie zum Ordner `[AEM installation directory]\crx-quickstart\conf\`. Öffnen Sie die Datei „sling.properties“ zur Bearbeitung. Wenn Sie `[AEM installation directory]\crx-quickstart\bin\start.bat`zum Starten einer AEM-Instanz verwenden, bearbeiten Sie die sling.properties-Datei unter `[AEM_root]\crx-quickstart\`. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:<br/>  `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br /> `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br />
   1. `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Speichern und schließen Sie die Datei. <br/>
   

1. 
   </p>