---
title: Dienst zur automatischen Formularkonvertierung konfigurieren
description: Bereiten Sie Ihre AEM-Instanz für die Verwendung des Dienstes zur automatischen Formularkonvertierung vor
translation-type: tm+mt
source-git-commit: c552f4073ac88ca9016a746116a27a5898df7f7d

---


# Dienst zur automatischen Formularkonvertierung konfigurieren{#about-this-help}

In dieser Hilfe wird beschrieben, wie ein AEM-Administrator den Dienst zur automatischen Formularkonvertierung konfigurieren kann, um die Konvertierung von PDF-Formularen in adaptive Formulare zu automatisieren. Diese Hilfe richtet sich an IT- und AEM-Administratoren in Ihrem Unternehmen. Benutzer dieser Hilfe sollten mit den folgenden Technologien vertraut sein:

* Installieren, Konfigurieren und Verwalten von Adobe Experience Manager- und AEM-Paketen,

* Verwenden von Linux- und Microsoft Windows-Betriebssystemen,

* Konfigurieren von SMTP-Mailservern

>[!VIDEO](https://video.tv.adobe.com/v/29267/)

**Sehen Sie sich das Video an oder lesen Sie den Artikel zum Konfigurieren des Dienstes für die automatische Formularkonvertierung**

## Einstieg{#onboarding}

Der Dienst steht AEM 6.4 Forms und AEM 6.5 Forms On-Premise-Kunden sowie Unternehmenskunden von Adobe Managed Service kostenlos zur Verfügung. Sie können sich an das Adobe Sales-Team oder Ihren Adobe-Vertreter wenden, um Zugriff auf den Service anzufordern.

Adobe ermöglicht den Zugriff für Ihre Organisation und stellt der in Ihrer Organisation als Administrator genannten Person die erforderlichen Berechtigungen zur Verfügung. Der Administrator kann den AEM Forms-Entwicklern (Benutzern) Ihrer Organisation Zugriff gewähren, um eine Verbindung zum Dienst herzustellen.

## Voraussetzungen {#prerequisites}

Für die Verwendung des Dienstes für die automatische Formularkonvertierung ist Folgendes erforderlich:

* Der Dienst zur automatischen Formularkonvertierung muss für Ihre Organisation aktiviert sein
* Ein Adobe ID-Konto mit Administratorrechten für den Konvertierungsdienst
* Eine betriebsbereite AEM 6.4- oder AEM 6.5-Autoreninstanz mit dem neuesten AEM Service Pack
* Ein AEM-Benutzer (in Ihrer AEM-Instanz), der Mitglied der Gruppe „forms-user“ ist

## Einrichten der Arbeitsumgebung {#setuptheservice}

Bereiten Sie vor der Verwendung des Dienstes Ihre AEM-Autoreninstanz für die Verbindung mit dem in Adobe Cloud ausgeführten Dienst vor. Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um Ihre Instanz für den Dienst vorzubereiten:

1. [Herunterladen und Installieren von AEM 6.4 oder AEM 6.5](#aemquickstart)
1. [Herunterladen und Installieren des neuesten AEM Service Packs](#servicepack)
1. [Herunterladen und Installieren des neuesten Add-On-Pakets für AEM Forms](#downloadaemformsaddon)
1. [Erstellen benutzerdefinierter Designs und Vorlagen](#referencepackage)

### Herunterladen und Installieren von AEM 6.4 oder AEM 6.5 {#aemquickstart}


Der Dienst zur automatischen Formularkonvertierung wird auf der AEM-Autoreninstanz ausgeführt. Sie benötigen AEM 6.4 oder AEM 6.5, um eine AEM-Autoreninstanz einzurichten. Wenn Sie AEM nicht eingerichtet haben, laden Sie es von den folgenden Speicherorten herunter:

* Wenn Sie bereits ein AEM-Kunde sind, laden Sie AEM 6.4 oder AEM 6.5 von der [Adobe Licensing Website](http://licensing.adobe.com) herunter.

* Wenn Sie ein Adobe-Partner sind, fordern Sie über das [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) AEM 6.4 oder AEM 6.5 an.

Anweisungen zum Einrichten einer AEM- Autoreninstanz finden Sie nach dem Herunterladen von AEM unter [Bereitstellen und Verwalten](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Herunterladen und Installieren des neuesten AEM Service Packs{#servicepack}

Laden Sie das aktuelle AEM Service Pack herunter und installieren Sie es. For detailed instructions see,  or [AEM 6.4 Service Pack Release Notes](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) or [AEM 6.5 Service Pack Release Notes](https://helpx.adobe.com/experience-manager/6-5/release-notes/sp-release-notes.html).

### Herunterladen und Installieren des Add-On-Pakets für AEM Forms  {#downloadaemformsaddon}

Eine AEM-Instanz enthält grundlegende Formularfunktionen. Der Konvertierungsdienst erfordert sämtliche Funktionen von AEM Forms. Laden Sie das AEM Forms-Add-On-Paket herunter und installieren Sie es, um alle Funktionen von AEM Forms nutzen zu können. Das Paket ist erforderlich, um den Konvertierungsdienst einzurichten und auszuführen. Detaillierte Anweisungen finden Sie unter [Installieren und Konfigurieren von Datenerfassungsfunktionen](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html).

>[!NOTE]
> Wenn Sie bereits Benutzer des Dienstes für die automatische Formularkonvertierung sind, installieren Sie das neueste AEM Forms-Add-on, um den Dienst weiterhin nutzen zu können. Das Connector-Paket wird mit dem AEM Forms Add-On-Paket zusammengeführt. Das zusätzliche Connector-Paket ist nicht mehr erforderlich.
> Stellen Sie sicher, dass Sie nach der Installation des Add-On-Pakets die obligatorischen Konfigurationen nach der Installation durchführen.


### Erstellen benutzerdefinierter Designs und Vorlagen{#referencepackage}

Wenn Sie AEM im [Produktionsmodus ](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) (nosamplecontent-Ausführungsmodus) starten, werden die Referenzpakete nicht installiert. Die Referenzpakete enthalten Beispieldesigns und -vorlagen. Für den Dienst für die automatische Formularkonvertierung sind mindestens ein Design und eine Vorlage erforderlich, um ein PDF-Formular in ein adaptives Formular zu konvertieren. Erstellen Sie ein eigenes benutzerdefiniertes Design und eine eigene Vorlage und zeigen Sie auf [Dienstkonfiguration](#configure-the-cloud-service), um benutzerdefinierte Vorlagen und Designs zu verwenden, bevor Sie den Dienst verwenden.

## Konfigurieren des Dienstes{#configure-the-service}

Bevor Sie mit der Konfiguration des Dienstes fortfahren und Ihre lokale Instanz mit dem in Adobe Cloud ausgeführten Dienst verbinden, sollten Sie sich über die Personen und Berechtigungen informieren, die für die Verbindung mit dem Dienst erforderlich sind. Der Dienst verwendet zwei verschiedene Arten von Personen: Administratoren und Entwickler:

* **Administratoren**: Administratoren sind für die Verwaltung der Adobe-Software und -Dienste für ihre Organisation verantwortlich. Administratoren gewähren Entwicklern in ihrer Organisation Zugriff zur Herstellung einer Verbindung zum Dienst für die automatische Formularkonvertierung, der in Adobe Cloud ausgeführt wird. Wenn ein Administrator für ein Unternehmen bereitgestellt wird, erhält der Administrator eine E-Mail mit dem Titel **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Wenn Sie Administrator sind, überprüfen Sie Ihr Postfach auf E-Mails mit dem oben genannten Titel und fahren Sie fort mit dem [ Gewähren des Zugriffs für Entwickler Ihrer Organisation](#adduseranddevs).

![E-Mail zur Gewährung des Administratorzugriffs](assets/admin-console-adobe-io-access-grantedx75.png)

* **Entwickler**: Ein Entwickler verbindet eine lokale AEM Forms-Autoreninstanz mit dem Dienst für die automatische Formularkonvertierung, der in der Adobe Cloud ausgeführt wird. Wenn ein Administrator einem Entwickler Rechte zum Herstellen einer Verbindung zum Dienst für die automatische Formularkonvertierung gewährt, wird eine E-Mail mit dem Titel „Sie haben jetzt Entwicklerzugriff zum Verwalten der Adobe API-Integrationen für Ihr Unternehmen“ an den Entwickler gesendet. Wenn Sie Entwickler sind, überprüfen Sie Ihr Postfach auf E-Mails mit dem oben genannten Titel und fahren Sie mit dem [Verbinden Ihrer lokalen AEM-Instanz mit dem Dienst für die automatische Formularkonvertierung in Adobe Cloud](#connectafcadobeio) fort.

![E-Mail zur Gewährung des Entwicklerzugriffs](assets/email-developer-accessx94.png)

### (Nur für Administratoren) Gewähren des Zugriffs für Entwickler in Ihrer Organisation{#adduseranddevs}

Nachdem Adobe den Zugriff für Ihr Unternehmen aktiviert und dem Administrator die erforderlichen Berechtigungen erteilt hat, kann sich der Administrator bei der Admin-Konsole anmelden (detaillierte Anweisungen unten), ein Profil erstellen und Entwickler zum Profil hinzufügen. Entwickler können eine lokale Instanz von AEM Forms mit dem Dienst für die automatische Formularkonvertierung in Adobe Cloud verbinden.

Entwickler sind Mitglieder Ihrer Organisation, die den Konvertierungsdienst ausführen. Nur Entwickler, die dem Dienstprofil für die automatische Formularkonvertierung von Adobe hinzugefügt wurden, sind berechtigt, den Dienst für die automatische Formularkonvertierung zu verwenden. Führen Sie die folgenden Schritte aus, um ein Profil zu erstellen und ihm Entwickler hinzuzufügen:

1. Melden Sie sich bei [Admin Console](https://adminconsole.adobe.com/) an. Melden Sie sich mit der **Adobe ID** des für die Verwendung des Dienstes für die automatische Formularkonvertierung bereitgestellten Administrators an. Verwenden Sie keine andere ID oder Federated ID, um sich anzumelden.
1. Klicken Sie auf die **[!UICONTROL Automated Forms Conversion]** Option.
1. Klicken Sie auf **[!UICONTROL New Profile]** die **[!UICONTROL Products]** Registerkarte.
1. Geben Sie **[!UICONTROL Name]**, **[!UICONTROL Display Name]** und **[!UICONTROL Description]** für das Profil an. Klicken Sie auf **[!UICONTROL Done]**. Ein Profil wird erstellt.

   ![Geben Sie Details für das neue Profil an.](assets/create-new-profile-details.png)

1. Fügen Sie Entwickler zum Profil hinzu. Hinzufügen der Entwickler:
   1. In der [Admin Console](https://adminconsole.adobe.com/enterprise), wechseln Sie zur Registerkarte „Übersicht“.
   1. Klicken Sie auf **[!UICONTROL Assign Developers]** die gewünschte Produktkarte.
   1. Geben Sie die E-Mail-Adresse des Entwicklers sowie optional den Vor- und Nachnamen ein.
   1. Wählen Sie „Produktprofile“. Tippen Sie auf **[!UICONTROL Save]**.

Wiederholen Sie die obigen Schritte für alle Benutzer.  Weitere Informationen zum Hinzufügen von Entwicklern finden Sie unter [Entwickler verwalten](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Sobald ein Administrator Entwickler zum Adobe I/O-Profil hinzufügt, werden die Entwickler per E-Mail benachrichtigt. Nach Erhalt der E-Mail können die Entwickler eine [lokale AEM Forms-Instanz mit dem Dienst für die automatische Formularkonvertierung in Adobe Cloud verbinden](#connectafcadobeio).

### (Nur für Entwickler) Verbinden Ihrer lokalen AEM Forms-Instanz mit dem Dienst für die automatische Formularkonvertierung in Adobe Cloud{#connectafcadobeio}

Nachdem ein Administrator Ihnen Entwicklerzugriff gewährt hat, können Sie Ihre lokale AEM Forms-Instanz mit dem in Adobe Cloud ausgeführten Dienst für die automatische Formularkonvertierung verbinden. Führen Sie die folgenden Schritte in der angegebenen Reihenfolge aus, um Ihre AEM Forms-Instanz mit dem Dienst zu verbinden:

* [Konfigurieren der E-Mail-Benachrichtigungen](configure-service.md#configureemailnotification)
* [ Benutzer zur Gruppe „forms-users“ hinzufügen](#adduserstousergroup)
* [Öffentliche Zertifikate abrufen](#obtainpubliccertificates)
* [Adobe I/O-Integration erstellen](#createintegration)
* [Konfigurieren des Cloud-Dienstes](configure-service.md#configure-the-cloud-service)

#### Konfigurieren der E-Mail-Benachrichtigungen{#configureemailnotification}

Der Dienst für die automatische Formularkonvertierung verwendet den Day CQ-Mail-Dienst zum Senden von E-Mail-Benachrichtigungen. Diese E-Mail-Benachrichtigungen enthalten Informationen zu erfolgreichen oder fehlgeschlagenen Konvertierungen. Wenn Sie keine Benachrichtigung erhalten möchten, überspringen Sie diese Schritte. Führen Sie die folgenden Schritte aus, um den Day CQ Mail-Dienst zu konfigurieren: 

1. Wechseln Sie zum AEM Configuration Manager unter `http://localhost:4502/system/console/configMgr`
1. Öffnen Sie die Konfiguration des Day CQ Mail Service. Geben Sie einen Wert für die Felder **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** und **[!UICONTROL From address]** an. Klicken Sie auf **[!UICONTROL Save]**.

   Informationen zum Hostnamen und zum Port des SMTP-Servers erhalten Sie von Ihrem E-Mail-Dienstanbieter oder IT-Administrator. Sie können eine beliebige gültige E-Mail-Adresse im Feld „Von“ verwenden. Zum Beispiel Benachrichtigung@example.com oder donotreply@example.com.

1. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration. Geben Sie im Feld **[!UICONTROL Domains]** den tatsächlichen Hostnamen/die IP-Adresse und die Portnummer für lokale Instanzen sowie Autoren- und Veröffentlichungsinstanzen an. Klicken Sie auf **[!UICONTROL Save]**.

#### Benutzer zur Formularbenutzergruppe hinzufügen {#adduserstousergroup}

Geben Sie im Profil des AEM-Benutzers, der den Dienst ausführen soll, eine E-Mail-Adresse an. Stellen Sie sicher, dass der Benutzer Mitglied der Gruppe [forms-users](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) ist. E-Mails werden an die E-Mail-Adresse des Benutzers gesendet, der die Konvertierung ausführt. So geben Sie eine E-Mail-Adresse für den Benutzer an und fügen den Benutzer der Formularbenutzergruppe hinzu:

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz als AEM-Administrator an. Verwenden Sie Ihre lokalen AEM-Anmeldeinformationen, um sich anzumelden. Verwenden Sie keine Adobe ID, um sich anzumelden. Tippen Sie auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Select a user designated to run the conversion service and tap **[!UICONTROL Properties]**. Die Seite „Benutzereinstellungen bearbeiten“ wird geöffnet.
1. Specify an email address in the **[!UICONTROL Email]** field and tap **[!UICONTROL Save]**. Die E-Mails werden nach erfolgreichem Abschluss oder fehlgeschlagener Konvertierung an die angegebene E-Mail-Adresse gesendet.
1. Tippen Sie auf die Registerkarte **Gruppen**. Geben Sie auf der Registerkarte „Gruppe auswählen“ die Gruppe **forms-users** ein und wählen Sie sie aus. Tippen Sie auf **Speichern und Schließen**. Der Benutzer ist jetzt Mitglied der Gruppe der Formularbenutzer.

#### Öffentliche Zertifikate abrufen{#obtainpubliccertificates}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in Adobe I/O.

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an. Navigieren Sie zu **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Tippen Sie auf **[!UICONTROL Create]**. The **[!UICONTROL Adobe IMS Technical Account Configuration]** page appears.

   ![Seite „Konfiguration des technischen Kontos von Adobe IMS“](assets/adobe-ims-technical-account-configuration.png)

1. Wählen Sie **[!UICONTROL Automated Forms Conversion Service]** in der Cloud-Lösung aus.

1. Aktivieren Sie das **[!UICONTROL Create new certificate]** Kontrollkästchen und geben Sie einen Alias an. Der Alias dient als Name des Dialogfelds. Tippen Sie auf **[!UICONTROL Create certificate]**. Ein Dialogfeld wird angezeigt. Klicken Sie auf **[!UICONTROL OK]**. Das Zertifikat wird erstellt.

1. Tap **[!UICONTROL Download Public Key]** and save the *AEM-Adobe-IMS.crt* certificate file on your machine. Die Zertifikatdatei wird verwendet, um die [Integration auf Adobe-E/A-Konsole zu erstellen](#createintegration). Tippen Sie auf **[!UICONTROL Next]**.

1. Geben Sie Folgendes an:

   * Titel: Geben Sie einen Titel an. 
   * Autorisierungsserver [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)
   Lassen Sie die anderen Felder vorerst leer (Werte werden später bereitgestellt). Lassen Sie die Seite geöffnet.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### Adobe I/O-Integration erstellen {#createintegration}

Erstellen Sie eine Integration in Adobe I/O, um den Dienst für die automatische Formularkonvertierung zu verwenden. Die Integration generiert API-Schlüssel, Client Secret, Payload (JWT).

1. Melden Sie sich bei [https://console.adobe.io/](https://console.adobe.io/) an. Melden Sie sich mit Ihrer Adobe ID und Ihrem vom Administrator zu diesem Zweck bereitgestellten Entwicklerkonto bei der I/O-Konsole an.

1. Tippen Sie auf **[!UICONTROL View Integrations]**. Ein Bildschirm mit allen verfügbaren Integrationen wird angezeigt.
1. Select your organization from the drop-down under **[!UICONTROL Integrations]**. Tippen Sie auf **[!UICONTROL New Integration]**, wählen Sie **[!UICONTROL Access an API]** und dann auf **[!UICONTROL Continue]**.
1. Wählen Sie **[!UICONTROL Experience Cloud]** > **[!UICONTROL Automated Forms Conversion]** und tippen Sie auf **[!UICONTROL Continue]**. Wenn die Option „Automatische Formularkonvertierung“ für Sie deaktiviert ist, stellen Sie sicher, dass Sie die richtige Organisation aus dem Dropdown-Feld über der Option **[!UICONTROL Adobe Services]** ausgewählt haben. Wenn Sie Ihre Organisation nicht kennen, wenden Sie sich an Ihren Administrator.

   ![Automatische Formularkonvertierung auswählen](assets/create-new-integration.png)

1. Geben Sie den Namen und die Beschreibung für die Integration an. Tippen Sie auf **[!UICONTROL Select a File from your computer]** und laden Sie die Datei &quot;AEM-Adobe-IMS.crt&quot;hoch, die Sie im Abschnitt &quot;Öffentliche Zertifikate [abrufen](#obtainpubliccertificates) &quot;heruntergeladen haben.
1. Select the profile created while [granting access to developers of your organization](#adduseranddevs) and tap **[!UICONTROL Create Integration]**. Die Integration wird erstellt.
1. Tippen Sie **[!UICONTROL Continue to integration details]** auf , um die Integrationsinformationen Ansicht. Die Seite enthält API-Schlüssel, Client Secret und andere Informationen, die zum Verbinden Ihrer lokalen AEM-Instanz mit dem Dienst für die automatische Formularkonvertierung erforderlich sind. Die Informationen auf der Seite werden verwendet, um eine IMS-Konfiguration auf Ihrem lokalen Computer zu erstellen.

   ![API-Schlüssel, Client Secret und Nutzdaten einer Integration ](assets/integration-details.png)

1. Öffnen Sie die Seite IMS-Konfiguration auf Ihrer lokalen Instanz. Sie haben die Seite am Ende des Abschnitts [Öffentliche Zertifikate abrufen](#obtainpubliccertificates) geöffnet gelassen.

   ![Geben Sie Titel, API-Schlüssel, Client Secret und Nutzlast an.](assets/ims-configuration-details.png)

1. Geben Sie auf der technischen Seite von Adobe IMS den API-Schlüssel und das Client Secret an. Verwenden Sie die auf der Integrationsseite angegebenen Werte.

   **Verwenden Sie für Nutzdaten den Code auf der Registerkarte JWT der Integrationsseite.** Tippen Sie auf  **[!UICONTROL Save]**. Die IMS-Konfiguration wird erstellt. Schließen Sie die Integrationsseite.

   ![Verwenden der Werte des JWT-Felds für das Nutzlastfeld](assets/jwt.png)

   >[!CAUTION]
   >
   >Erstellen Sie nur eine IMS-Konfiguration. Erstellen Sie nicht mehr als eine IMS-Konfiguration.

1. Select the IMS configuration and tap **[!UICONTROL Check Health]**. Das folgende Dialogfeld wird angezeigt. Tippen Sie auf **[!UICONTROL Check]**. Bei erfolgreicher Verbindung wird die Meldung *Token erfolgreich abgerufen* angezeigt.

   ![Bei erfolgreicher Verbindung wird die Meldung „Token erfolgreich abgerufen“ angezeigt. ](assets/health-check.png)

   <br/> <br/>

#### Konfigurieren des Cloud-Dienstes{#configure-the-cloud-service}

Erstellen Sie eine Cloud-Dienstkonfiguration, um Ihre AEM-Instanz mit dem Konvertierungsdienst zu verbinden. Außerdem können Sie eine Vorlage, ein Design und Formularfragmente für eine Konvertierung angeben. Sie können mehrere Cloud-Service-Konfigurationen für jeden Formularsatz separat erstellen. Beispielsweise können Sie separate Konfigurationen für Formulare der Verkaufsabteilung und für Formulare für den Kundensupport erstellen. Führen Sie die folgenden Schritte aus, um ein eine Cloud-Service-Konfiguration zu erstellen:

1. Tippen Sie in Ihrer AEM Forms-Instanz auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Tap the **[!UICONTROL Global]** folder and tap **[!UICONTROL Create]**. Die Seite zum Erstellen der Konfiguration für die automatische Formularkonvertierung wird angezeigt. Die Konfiguration wird im Ordner „Global“ erstellt. Sie können die Konfiguration auch in einem anderen Ordner erstellen, der bereits vorhanden ist, oder einen neuen Ordner für Ihre Konfigurationen erstellen.

1. Geben Sie auf der **[!UICONTROL Create Automated Forms Conversion Configuration]** Seite einen Wert für die folgenden Felder ein und tippen Sie auf **[!UICONTROL Next]**.

   | Feld | Beschreibung |
   |--- |--- |
   | Titel | Eindeutiger Titel für die Konfiguration. Der Titel wird in der Benutzeroberfläche zum Starten der Konvertierung angezeigt. |
   | Name | Eindeutiger Name für die Konfiguration. Die Konfiguration wird im CRX-Repository unter dem angegebenen Namen gespeichert. Der Name kann mit dem Titel identisch sein. |
   | Position der Miniaturansicht | Position der Miniaturansicht für die Konfiguration. |
   | Dienst-URL | URL des Dienstes für die automatische Formularkonvertierung in Adobe Cloud. Verwenden Sie die URL `https://aemformsconversion.adobe.io/`. |
   | Vorlage | Standardvorlage für konvertierte Formulare. Sie können jederzeit eine andere Vorlage angeben, bevor Sie mit der Konvertierung beginnen. Eine Vorlage enthält die Grundstruktur und den Anfangsinhalt für ein adaptives Formular. Sie können eine Vorlage aus den standardmäßig bereitgestellten Vorlagen auswählen. Sie können auch eine benutzerdefinierte Vorlage erstellen. |
   | Design | Standarddesign für konvertierte Formulare. Sie können jederzeit ein anderes Design angeben, bevor Sie mit der Konvertierung beginnen.  Sie können auf das Symbol klicken, um ein standardmäßig bereitgestelltes Design auszuwählen. Sie können auch ein benutzerdefiniertes Design erstellen. |
   | Vorhandene Fragmente | Position vorhandener Fragmente, falls vorhanden. |
   | Benutzerdefiniertes Metamodell | Pfad der .schema.json-Datei des benutzerdefinierten Metamodells. |



1. Geben Sie auf der **[!UICONTROL Advanced]** Registerkarte der **[!UICONTROL Create Automated Forms Conversion Configuration]** Seite einen Wert für das folgende Feld an:

   <table>
   <thead>
   <tr>
   <th>Feld</th>
   <th>Beschreibung</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >Generieren des Datensatzdokuments</td>
   <td>Wählen Sie die Option zum automatischen Generieren des Datensatzdokuments für konvertierte Formulare. Die Option gilt nur für XFA-basierte Formulare (XDP- und PDF-Formulare). Wenn Sie diese Option aktivieren, können Sie nach dem Absenden eines Formulars Ihren Kunden die Möglichkeit geben, die von ihnen im Formular ausgefüllten Informationen in gedruckter Form oder als Dokument aufzubewahren, um sie später nachlesen zu können. Dies wird als Datensatzdokument bezeichnet.</td>
   </tr>
   <tr>
   <td>Analytics aktivieren</td>
   <td>Wählen Sie die Option aus, um Adobe Analytics für alle konvertierten Formulare zu aktivieren. Stellen Sie vor Verwendung der Option sicher, dass Adobe Analytics für Ihre AEM Forms-Instanz aktiviert ist.</td>
   </tr>
   </tbody>
   </table>

   * Wenn die Quelle ein XFA-basiertes Formular mit der Erweiterung .XDP ist, behält das Ausgabe-DOR das XFA-Layout bei, andernfalls verwendet der Konvertierungsdienst eine standardmäßig bereitgestellte Vorlage, um das DOR für andere XFA-basierte Formulare zu generieren.
   * Wenn ein XFA-Formular gesendet wird, werden die Übermittlungsdaten des Formulars als XML-Element oder Attribut gespeichert. Beispiel: `<Amount currency="USD"> 10.00 </Amount>`. Die Währung wird als Attribut, der Währungsbetrag 10,00 als Element gespeichert. Übermittlungsdaten adaptiver Formulare enthalten keine Attribute, sondern nur Elemente. Das bedeutet: Wenn ein XFA-basiertes Formular in ein adaptives Formular konvertiert wird, enthalten die Übermittlungsdaten des adaptiven Formulars ein Element für jedes dieser Attribute. Beispiel:

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Tippen Sie auf **[!UICONTROL Create]**. Die Cloud-Konfiguration wird erstellt. Damit ist Ihre AEM Forms-Instanz bereit, ältere Formulare in adaptive Formulare zu konvertieren.
