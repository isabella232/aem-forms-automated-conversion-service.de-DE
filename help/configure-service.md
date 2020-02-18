---
title: Konfigurieren des Dienstes "Automatisierte Formularkonvertierung"
description: Bereiten Sie Ihre AEM-Instanz für die Verwendung des Dienstes Automatisierte Formularkonvertierung vor
translation-type: tm+mt
source-git-commit: ef5789dabccc65dcf988b9424b435aa036017691

---


# Konfigurieren des Dienstes &quot;Automatisierte Formularkonvertierung&quot; {#about-this-help}

In dieser Hilfe wird beschrieben, wie ein AEM-Administrator den Dienst &quot;Automatisierte Formularkonvertierung&quot;konfigurieren kann, um die Konvertierung ihrer PDF-Formulare in adaptive Formulare zu automatisieren. Diese Hilfe richtet sich an IT- und AEM-Administratoren in Ihrem Unternehmen. Benutzer dieser Hilfe sollten mit den folgenden Technologien vertraut sein:

* Installieren, Konfigurieren und Verwalten von Adobe Experience Manager- und AEM-Paketen,

* Linux- und Microsoft Windows-Betriebssysteme,

* Konfigurieren von SMTP-Mail-Servern

>[!VIDEO](https://video.tv.adobe.com/v/29267/)

**Sehen Sie sich das Video an oder lesen Sie den Artikel zum Konfigurieren des Dienstes &quot;Automatisierte Formularkonvertierung&quot;**

## Einstieg{#onboarding}

Der Dienst steht Kunden von AEM 6.5 Forms und AEM 6.4 Forms On-Premise-Terminologiekunden und Adobe Managed Service-Unternehmenskunden kostenlos zur Verfügung. Sie können sich an das Adobe Sales Team oder Ihren Adobe-Kundenbetreuer wenden, um Zugriff auf den Dienst anzufordern.

Adobe ermöglicht den Zugriff auf Ihr Unternehmen und stellt die erforderlichen Berechtigungen für die Person bereit, die als Administrator in Ihrem Unternehmen benannt wurde. Der Administrator kann Ihren AEM Forms-Entwicklern (Benutzern) Ihres Unternehmens Zugriff auf die Verbindung zum Dienst gewähren.

## Voraussetzungen {#prerequisites}

Sie benötigen Folgendes, um den Automatisierten Forms-Konvertierungsdienst zu verwenden:

* Der Dienst für die automatisierte Formularkonvertierung ist für Ihr Unternehmen aktiviert
* Ein Adobe-ID-Konto mit Administratorrechten für den Konvertierungsdienst
* Eine Autoreninstanz für AEM 6.5 oder AEM 6.4 mit dem neuesten AEM Service Pack
* Ein AEM-Benutzer (auf Ihrer AEM-Instanz), der Mitglied der Forms-Benutzergruppe ist

## Einrichten der Umgebung {#setuptheservice}

Bevor Sie den Dienst verwenden, bereiten Sie Ihre AEM-Autoreninstanz darauf vor, eine Verbindung zu dem Dienst herzustellen, der in der Adobe Cloud ausgeführt wird. Führen Sie die folgenden Schritte in der aufgeführten Reihenfolge aus, um Ihre Instanz für den Dienst vorzubereiten:

1. [Herunterladen und Installieren von AEM 6.5 oder AEM 6.4](#aemquickstart)
1. [Laden Sie das neueste AEM Service Pack herunter und installieren Sie es](#servicepack)
1. [Herunterladen und Installieren des neuesten Add-On-Pakets für AEM Forms](#downloadaemformsaddon)
1. [Benutzerdefinierte Designs und Vorlagen erstellen](#referencepackage)

### Herunterladen und Installieren von AEM 6.5 oder AEM 6.4 {#aemquickstart}


Der Dienst &quot;Automatisierte Formularkonvertierung&quot;wird auf der AEM-Autoreninstanz ausgeführt. Sie benötigen AEM 6.5 oder AEM 6.4, um eine AEM-Autoreninstanz einzurichten. Wenn Sie AEM nicht ausgeführt haben, laden Sie es von den folgenden Speicherorten herunter:

* Wenn Sie bereits AEM-Kunde sind, laden Sie AEM 6.5 oder AEM 6.4 von der [Adobe Licensing-Website](http://licensing.adobe.com)herunter.

* Wenn Sie Adobe-Partner sind, verwenden Sie das [Adobe-Partnerschulungsprogramm](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) , um AEM 6.5 oder AEM 6.4 anzufordern.

Nach dem Herunterladen von AEM finden Sie Anweisungen zum Einrichten einer AEM-Autoreninstanz unter [Bereitstellen und Warten](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Download and install AEM latest Service Pack {#servicepack}

Laden Sie das neueste AEM Service Pack herunter und installieren Sie es. Ausführliche Anweisungen finden Sie in den Versionshinweisen[ zu ](https://helpx.adobe.com/experience-manager/6-5/release-notes/sp-release-notes.html)AEM 6.5 Service Pack oder [AEM 6.4 Service Pack-Versionshinweisen](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html).

### Download and install AEM Forms add-on package  {#downloadaemformsaddon}

Eine AEM-Instanz enthält grundlegende Formularfunktionen. Der Konvertierungsdienst erfordert sämtliche Funktionen von AEM Forms. Laden Sie das Add-On-Paket für AEM Forms herunter und installieren Sie es, um alle Funktionen von AEM Forms zu nutzen. Das Paket ist erforderlich, um den Konvertierungsdienst einzurichten und auszuführen. Detaillierte Anweisungen finden Sie unter [Installieren und Konfigurieren der Datenerfassungsfunktionen.](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Wenn Sie bereits Benutzer des Dienstes &quot;Automatisierte Formularkonvertierung&quot;sind, installieren Sie das neueste AEM Forms-Add-on, um den Dienst weiter zu verwenden. Das Connector-Paket wird mit dem AEM Forms Add-On-Paket zusammengeführt. Das zusätzliche Connector-Paket ist nicht mehr erforderlich.
> Stellen Sie sicher, dass Sie nach der Installation des Add-On-Pakets die erforderlichen Konfigurationen nach der Installation durchführen.


### Benutzerdefinierte Designs und Vorlagen erstellen {#referencepackage}

Wenn Sie AEM im [Produktionsmodus](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) starten (nicht im Ausführungsmodus für den Inhalt), werden die Referenzpakete nicht installiert. Die Referenzpakete enthalten Beispielthemen und Vorlagen. Für die Konvertierung eines PDF-Formulars in ein adaptives Formular ist mindestens ein Design und eine Vorlage erforderlich. Erstellen Sie ein benutzerdefiniertes Design und eine Vorlage Ihrer eigenen und Point- [Service-Konfiguration](#configure-the-cloud-service) , um benutzerdefinierte Vorlagen und Designs zu verwenden, bevor Sie den Dienst verwenden.

## Konfigurieren des Dienstes {#configure-the-service}

Bevor Sie den Dienst konfigurieren und Ihre lokale Instanz mit dem Dienst verbinden, der in der Adobe Cloud ausgeführt wird, sollten Sie sich mit den für die Verbindung mit dem Dienst erforderlichen Personen und Berechtigungen vertraut machen. Der Dienst verwendet zwei verschiedene Typen von Personen, Administratoren und Entwicklern:

* **Administratoren**: Administratoren sind für die Verwaltung von Adobe-Software und -Diensten für ihre Organisation zuständig. Administratoren gewähren Entwicklern in ihrem Unternehmen Zugriff auf die Verbindung zum Dienst für die automatisierte Formularkonvertierung, der in der Adobe Cloud ausgeführt wird. Wenn ein Administrator für ein Unternehmen bereitgestellt wird, erhält der Administrator eine E-Mail mit dem Titel **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Wenn Sie Administrator sind, suchen Sie in Ihrem Postfach nach einer E-Mail mit dem oben genannten Titel und [gewähren Sie den Entwicklern Ihres Unternehmens](#adduseranddevs)Zugriff.

![E-Mail mit Administratorzugriffsberechtigung](assets/admin-console-adobe-io-access-grantedx75.png)

* **Entwickler**: Ein Entwickler verbindet eine lokale AEM Forms-Autoreninstanz mit dem Dienst für die automatische Formularkonvertierung, der in der Adobe Cloud ausgeführt wird. Wenn ein Administrator einem Entwickler Berechtigungen zur Verbindung mit dem automatisierten Forms-Konvertierungsdienst erteilt, wird eine E-Mail mit dem Titel &quot;Sie haben jetzt Zugriff auf Entwickler, um Adobe API-Integrationen für Ihr Unternehmen zu verwalten&quot;an den Entwickler gesendet. Wenn Sie Entwickler sind, suchen Sie in Ihrem Postfach nach einer E-Mail mit dem oben genannten Titel und fahren Sie mit der [Verbindung Ihrer lokalen AEM-Instanz mit dem Automatisierten Forms-Konvertierungsdienst in Adobe Cloud fort.](#connectafcadobeio)

![Entwicklerzugriffsemail](assets/email-developer-accessx94.png)

### (Nur für Administratoren) Gewähren Sie Entwicklern Ihrer Organisation Zugriff {#adduseranddevs}

Nachdem Adobe den Zugriff für Ihr Unternehmen aktiviert und dem Administrator die erforderlichen Berechtigungen erteilt hat, kann sich der Administrator bei der Admin-Konsole anmelden (detaillierte Anweisungen unten), ein Profil erstellen und dem Profil Entwickler hinzufügen. Entwickler können eine lokale Instanz von AEM Forms mit dem Dienst für die automatische Formularkonvertierung in Adobe Cloud verbinden.

Entwickler sind Mitglieder Ihrer Organisation, die für die Ausführung des Konvertierungsdienstes vorgesehen sind. Nur die Entwickler, die dem Profil des Adobe Automated Forms Conversion-Dienstes hinzugefügt werden, sind berechtigt, den Dienst Automatisierte Formularkonvertierung zu verwenden. Führen Sie die folgenden Schritte aus, um ein Profil zu erstellen und ihm Entwickler hinzuzufügen:

1. Melden Sie sich bei der [Admin-Konsole](https://adminconsole.adobe.com/)an. Verwenden Sie die **Adobe-ID** des Administrators, der für die Anmeldung mit dem Automatisierten Forms-Konvertierungsdienst bereitgestellt wurde. Keine andere ID oder Federated ID zur Anmeldung verwenden.
1. Klicken Sie auf die **[!UICONTROL Automated Forms Conversion]** Option.
1. Klicken Sie auf **[!UICONTROL New Profile]** die **[!UICONTROL Products]** Registerkarte.
1. Geben Sie **[!UICONTROL Name]**, **[!UICONTROL Display Name]** und **[!UICONTROL Description]** für das Profil an. Klicken Sie auf **[!UICONTROL Done]**. Ein Profil wird erstellt.

   ![Geben Sie Details für das neue Profil an.](assets/create-new-profile-details.png)

1. Fügen Sie dem Profil Entwickler hinzu. So fügen Sie die Entwickler hinzu:
   1. Navigieren Sie in der [Admin-Konsole](https://adminconsole.adobe.com/enterprise)zur Registerkarte Übersicht.
   1. Klicken Sie auf **[!UICONTROL Assign Developers]** die gewünschte Produktkarte.
   1. Geben Sie die E-Mail-Adresse und optional den Vor- und Nachnamen der Entwickler ein.
   1. Wählen Sie Produktprofile. Tippen Sie auf **[!UICONTROL Save]**.

Wiederholen Sie diese Schritte für alle Benutzer.  Weitere Informationen zum Hinzufügen von Entwicklern finden Sie unter Entwickler [verwalten](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Sobald ein Administrator Entwickler zum Adobe-E/A-Profil hinzufügt, werden die Entwickler per E-Mail benachrichtigt. Nach Erhalt der E-Mail können die Entwickler eine lokale AEM Forms-Instanz mit dem Automatisierten Forms-Konvertierungsdienst in Adobe Cloud [verbinden](#connectafcadobeio).

### (Nur für Entwickler) Verbinden Sie Ihre lokale AEM Forms-Instanz mit dem Dienst für die automatisierte Formularkonvertierung in Adobe Cloud {#connectafcadobeio}

Nachdem ein Administrator den Entwicklerzugriff bereitgestellt hat, können Sie Ihre lokale AEM Forms-Instanz mit dem Konvertierungsdienst für automatisierte Formulare verbinden, der in der Adobe Cloud ausgeführt wird. Führen Sie die folgenden Schritte in der aufgeführten Reihenfolge aus, um Ihre AEM Forms-Instanz mit dem Dienst zu verbinden:

* [Konfigurieren Sie E-Mail-Benachrichtigungen](configure-service.md#configureemailnotification)
* [Benutzer zur Gruppe der Formularbenutzer hinzufügen](#adduserstousergroup)
* [Öffentliche Zertifikate abrufen](#obtainpubliccertificates)
* [Adobe I/O-Integration erstellen](#createintegration)
* [Cloud-Dienst konfigurieren](configure-service.md#configure-the-cloud-service)

#### E-Mail-Benachrichtigung konfigurieren {#configureemailnotification}

Der automatisierte Forms-Konvertierungsdienst verwendet den Day CQ-E-Mail-Dienst zum Senden von E-Mail-Benachrichtigungen. Diese E-Mail-Benachrichtigungen enthalten Informationen zu erfolgreichen oder fehlgeschlagenen Konvertierungen. Wenn Sie sich dafür entscheiden, keine Benachrichtigung zu erhalten, überspringen Sie diese Schritte. Führen Sie die folgenden Schritte aus, um den Day CQ Mail Service zu konfigurieren:

1. Gehen Sie zu AEM Configuration Manager unter `http://localhost:4502/system/console/configMgr`
1. Öffnen Sie die Konfiguration des Day CQ Mail Service. Geben Sie einen Wert für die Felder **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** und **[!UICONTROL From address]** an. Klicken Sie auf **[!UICONTROL Save]**.

   Sie können sich an Ihren E-Mail-Serviceanbieter oder IT-Administrator wenden, um Informationen zu Hostnamen und Anschluss des SMTP-Servers zu erhalten. Sie können jede gültige E-Mail-Adresse im Feld &quot;Von&quot;verwenden. Beispiel: notification@example.com oder donotreply@example.com.

1. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration. In the **[!UICONTROL Domains]** field, specify the actual host name or IP address and port number for local, author, and publish instances. Klicken Sie auf **[!UICONTROL Save]**.

#### Benutzer zur Gruppe der Formularbenutzer hinzufügen {#adduserstousergroup}

Geben Sie eine E-Mail-Adresse im Profil des AEM-Benutzers an, der zum Ausführen des Dienstes bestimmt ist. Stellen Sie sicher, dass der Benutzer Mitglied der [Forms-Benutzergruppe](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) ist. E-Mails werden an die E-Mail-Adresse des Benutzers gesendet, der die Konversion ausführt. So geben Sie eine E-Mail-Adresse für den Benutzer an und fügen Sie der Gruppe des Formularbenutzers Benutzer hinzu:

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz als AEM-Administrator an. Verwenden Sie Ihre lokalen AEM-Anmeldedaten, um sich anzumelden. Verwenden Sie für die Anmeldung keine Adobe-ID. Tippen Sie auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Wählen Sie einen Benutzer aus, der zum Ausführen des Konvertierungsdiensts bestimmt ist, und tippen Sie auf **[!UICONTROL Properties]**. Die Seite Edit User Settings (Benutzereinstellungen bearbeiten) wird geöffnet.
1. Geben Sie eine E-Mail-Adresse in das **[!UICONTROL Email]** Feld ein und tippen Sie auf **[!UICONTROL Save]**. Die E-Mails werden nach erfolgreichem Abschluss oder fehlgeschlagener Konvertierung an die angegebene E-Mail-Adresse gesendet.
1. Tap the **Groups** tab. Geben Sie auf der Registerkarte Gruppe auswählen die Gruppe **forms-users** ein. Tap **Save &amp; Close**. Der Benutzer ist jetzt Mitglied der Gruppe der Benutzer von Formularen.

#### Öffentliche Zertifikate abrufen {#obtainpubliccertificates}

Ein öffentliches Zertifikat ermöglicht Ihnen die Authentifizierung Ihres Profils in Adobe I/O.

1. Melden Sie sich bei Ihrer AEM Forms-Autoreninstanz an. Navigieren Sie zu **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Tippen Sie auf **[!UICONTROL Create]**. The **[!UICONTROL Adobe IMS Technical Account Configuration]** page appears.

   ![Die Seite &quot;Konfiguration des technischen Adobe IMS-Kontos&quot;](assets/adobe-ims-technical-account-configuration.png)

1. Wählen Sie **[!UICONTROL Automated Forms Conversion Service]** in der Cloud-Lösung aus.

1. Aktivieren Sie das **[!UICONTROL Create new certificate]** Kontrollkästchen und geben Sie einen Alias an. Der Alias dient als Name des Dialogfelds. Tippen Sie auf **[!UICONTROL Create certificate]**. Ein Dialogfeld wird angezeigt. Klicken Sie auf **[!UICONTROL OK]**. Das Zertifikat wird erstellt.

1. Tippen Sie auf **[!UICONTROL Download Public Key]** und speichern Sie die *AEM-Adobe-IMS.crt* -Zertifikatdatei auf Ihrem Computer. Die Zertifikatdatei wird zum [Erstellen der Integration in der Adobe-E/A-Konsole](#createintegration)verwendet. Tippen Sie auf **[!UICONTROL Next]**.

1. Geben Sie Folgendes an:

   * Titel: Geben Sie einen Titel an.
   * Authorization Server: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)
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

Um den Dienst &quot;Automatisierte Formularkonvertierung&quot;zu verwenden, erstellen Sie eine Integration in Adobe I/O. Die Integration erzeugt API-Schlüssel, geheimer Clientschlüssel, Payload (JWT).

1. Melden Sie sich bei [https://console.adobe.io/](https://console.adobe.io/)an. Verwenden Sie Ihre Adobe-ID, das Entwicklerkonto, das Ihr Administrator zur Anmeldung bei der Adobe I/O-Konsole eingerichtet hat.

1. Tippen Sie auf **[!UICONTROL View Integrations]**. Ein Bildschirm mit allen verfügbaren Integrationen wird angezeigt.
1. Wählen Sie Ihre Organisation aus der Dropdownliste unter **[!UICONTROL Integrations]**. Tippen Sie auf **[!UICONTROL New Integration]**, wählen Sie **[!UICONTROL Access an API]** und dann auf **[!UICONTROL Continue]**.
1. Wählen Sie **[!UICONTROL Experience Cloud]** > **[!UICONTROL Automated Forms Conversion]** und tippen Sie auf **[!UICONTROL Continue]**. Wenn die Option &quot;Automatisierte Formularkonvertierung&quot;für Sie deaktiviert ist, stellen Sie sicher, dass Sie im Dropdown-Feld über der **[!UICONTROL Adobe Services]** Option die richtige Organisation ausgewählt haben. Wenn Sie Ihr Unternehmen nicht kennen, wenden Sie sich an Ihren Administrator.

   ![Automatisierte Formularkonvertierung auswählen](assets/create-new-integration.png)

1. Geben Sie den Namen und die Beschreibung für die Integration an. Tippen Sie auf **[!UICONTROL Select a File from your computer]** und laden Sie die Datei &quot;AEM-Adobe-IMS.crt&quot;hoch, die Sie im Abschnitt [Öffentliche Zertifikate](#obtainpubliccertificates) abrufen heruntergeladen haben.
1. Wählen Sie das erstellte Profil aus, während Sie Entwicklern Ihres Unternehmens Zugriff [gewähren](#adduseranddevs) , und tippen Sie auf **[!UICONTROL Create Integration]**. Die Integration wird erstellt.
1. Tippen Sie **[!UICONTROL Continue to integration details]** auf , um die Integrationsinformationen anzuzeigen. Die Seite enthält API-Schlüssel, geheimen Clientschlüssel und andere Informationen, die erforderlich sind, um Ihre lokale AEM-Instanz mit dem Automatisierten Forms-Konvertierungsdienst zu verbinden. Die Informationen auf der Seite werden verwendet, um eine IMS-Konfiguration auf Ihrem lokalen Computer zu erstellen.

   ![API-Schlüssel, geheimer Clientschlüssel und Nutzdaten einer Integration](assets/integration-details.png)

1. Öffnen Sie die Seite &quot;IMS-Konfiguration&quot;auf Ihrer lokalen Instanz. Sie haben die Seite am Ende des Abschnitts geöffnet, [öffentliches Zertifikat](#obtainpubliccertificates)abrufen.

   ![Geben Sie Titel, API-Schlüssel, geheimen Clientschlüssel und Payload an ](assets/ims-configuration-details.png)

1. Geben Sie auf der Seite &quot;Adobe IMS Technical&quot;den API-Schlüssel und den geheimen Clientschlüssel ein. Verwenden Sie die auf der Integrationsseite angegebenen Werte.

   **Verwenden Sie für die Nutzlast den auf der Registerkarte &quot;JWT&quot;der Integrationsseite bereitgestellten Code.** Tippen Sie auf  **[!UICONTROL Save]**. Die IMS-Konfiguration wird erstellt. Schließen Sie die Integrationsseite.

   ![Werte des JWT-Felds für das Payload-Feld verwenden](assets/jwt.png)

   >[!CAUTION]
   >
   >Erstellen Sie nur eine IMS-Konfiguration. Erstellen Sie nicht mehr als eine IMS-Konfiguration.

1. Wählen Sie die IMS-Konfiguration und tippen Sie auf **[!UICONTROL Check Health]**. Das folgende Dialogfeld wird angezeigt. Tippen Sie auf **[!UICONTROL Check]**. Bei erfolgreicher Verbindung wird die Meldung *Token erfolgreich* abgerufen angezeigt.

   ![Bei erfolgreicher Verbindung wird die Meldung über das erfolgreich abgerufene Token angezeigt. ](assets/health-check.png)

   <br/> <br/>

#### Cloud-Dienst konfigurieren {#configure-the-cloud-service}

Erstellen Sie eine Cloud-Dienstkonfiguration, um Ihre AEM-Instanz mit dem Konvertierungsdienst zu verbinden. Sie können auch Vorlagen, Designs und Formularfragmente für eine Konvertierung angeben. Sie können mehrere Cloud-Dienstkonfigurationen für jeden Formularsatz einzeln erstellen. Sie können beispielsweise eine separate Konfiguration für Formulare der Verkaufsabteilung und eine separate Konfiguration für Formulare des Kundensupports verwenden. Führen Sie die folgenden Schritte aus, um eine Cloud-Dienstkonfiguration zu erstellen:

1. Tippen Sie in Ihrer AEM Forms-Instanz auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Tippen Sie auf den **[!UICONTROL Global]** Ordner und dann auf **[!UICONTROL Create]**. Die Seite zum Erstellen der Konfiguration der automatisierten Formularkonvertierung wird angezeigt. Die Konfiguration wird im Ordner &quot;Global&quot;erstellt. Sie können die Konfiguration auch in einem anderen Ordner erstellen, der bereits vorhanden ist, oder einen neuen Ordner für Ihre Konfigurationen erstellen.

1. Geben Sie auf der **[!UICONTROL Create Automated Forms Conversion Configuration]** Seite einen Wert für die folgenden Felder ein und tippen Sie auf **[!UICONTROL Next]**.

   | Feld | Beschreibung |
   |--- |--- |
   | Titel | Eindeutiger Titel für die Konfiguration. Der Titel wird in der Benutzeroberfläche angezeigt, die zum Starten der Konvertierung verwendet wird. |
   | Name | Eindeutiger Name für die Konfiguration. Die Konfiguration wird im CRX-Repository mit dem angegebenen Namen gespeichert. Der Name kann mit dem Titel identisch sein. |
   | Position der Miniaturansicht | Speicherort der Miniaturansicht für die Konfiguration. |
   | Dienst-URL | URL des Dienstes &quot;Automatisierte Formularkonvertierung&quot;in Adobe Cloud. Verwenden Sie die `https://aemformsconversion.adobe.io/` URL. |
   | Vorlage | Standardvorlage, die auf konvertierte Formulare anzuwenden ist. Sie können vor Beginn der Konvertierung immer eine andere Vorlage angeben. Eine Vorlage enthält eine grundlegende Struktur und anfänglichen Inhalt für ein adaptives Formular. Sie können eine Vorlage aus den standardmäßig bereitgestellten Vorlagen auswählen. Sie können auch eine benutzerdefinierte Vorlage erstellen. |
   | Design | Standarddesign für konvertierte Formulare. Sie können vor Beginn der Konvertierung immer ein anderes Design angeben.  Sie können auf das Symbol klicken, um ein standardmäßig bereitgestelltes Design auszuwählen. Sie können auch ein benutzerdefiniertes Design erstellen. |
   | Vorhandene Fragmente | Speicherort der vorhandenen Fragmente, falls vorhanden. |
   | Benutzerdefiniertes Meta-Modell | Pfad der Datei .schema.json des benutzerdefinierten Meta-Modells. |



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
   <td >Generieren von Dokument aus Datensatz</td>
   <td>Wählen Sie die Option zum automatischen Generieren des Datensatzdokuments für konvertierte Formulare. Die Option ist nur für XFA-basierte Formulare (XDP- und PDF-Formulare) verfügbar. Wenn Sie die Option aktivieren, können Sie Ihren Kunden nach dem Senden eines Formulars gestatten, einen Datensatz zu speichern, der als Druckkopie oder als Dokument vorliegt, der die Informationen enthält, die sie im Formular für ihre künftige Referenz ausgefüllt haben. Dies wird als Datensatzdokument bezeichnet.</td>
   </tr>
   <tr>
   <td>Analyse aktivieren</td>
   <td>Wählen Sie die Option, um Adobe Analytics für alle konvertierten Formulare zu aktivieren. Bevor Sie diese Option verwenden, stellen Sie sicher, dass Adobe Analytics für Ihre AEM Forms-Instanz aktiviert ist.</td>
   </tr>
   </tbody>
   </table>

   * Wenn es sich bei der Quelle um ein XFA-basiertes Formular mit der Erweiterung .XDP handelt, behält die Ausgabe-DOR das XFA-Layout bei, andernfalls verwendet der Konvertierungsdienst eine vordefinierte Vorlage, um DOR für andere XFA-basierte Formulare zu generieren.
   * Wenn ein XFA-Formular gesendet wird, werden die Senden-Daten des Formulars als XML-Element oder Attribut gespeichert. Beispiel, `<Amount currency="USD"> 10.00 </Amount>`. Die Währung wird als Attribut und Währungsbetrag gespeichert, 10.00 wird als Element gespeichert. Die Übermittlungsdaten eines adaptiven Formulars haben keine Attribute, sondern nur Elemente. Wenn also ein XFA-basiertes Formular in ein adaptives Formular konvertiert wird, enthalten die Daten zum Senden des adaptiven Formulars ein Element für jedes dieser Attribute. Beispiel:

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Tippen Sie auf **[!UICONTROL Create]**.  Die Cloud-Konfiguration wird erstellt. Ihre AEM Forms-Instanz ist bereit, mit der Konvertierung älterer Formulare in adaptive Formulare zu beginnen.
