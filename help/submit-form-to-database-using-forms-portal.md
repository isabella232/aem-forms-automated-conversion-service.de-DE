---
title: Senden adaptiver Formulare mithilfe des Formularportals an die Datenbank
description: Erweitern Sie das Standard-Metamodell, um Muster, Validierungen und Entitäten hinzuzufügen, die für Ihre Organisation spezifisch sind, und Konfigurationen auf adaptive Formularfelder anzuwenden, während Sie den Dienst für die automatische Formularkonvertierung ausführen.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: c552f4073ac88ca9016a746116a27a5898df7f7d

---


# Integrieren adaptiver Formulare in Datenbank mithilfe von Forms Portal {#submit-forms-to-database-using-forms-portal}

Mit dem Dienst zur automatischen Formularkonvertierung können Sie ein nicht-interaktives PDF-Formular, ein Acro Form oder ein XFA-basiertes PDF-Formular in ein adaptives Formular konvertieren. Während Sie den Konvertierungsprozess starten, haben Sie die Möglichkeit, ein adaptives Formular mit oder ohne Datenbindung zu generieren.

Wenn Sie ein adaptives Formular ohne Datenbindungen generieren möchten, können Sie nach der Konvertierung das adaptive Formular in ein Formulardatenmodell, ein XML-Schema oder ein JSON-Schema integrieren. Wenn Sie jedoch ein adaptives Formular mit Datenbindungen generieren, ordnet der Konvertierungsdienst die adaptiven Formulare automatisch einem JSON-Schema zu und erstellt eine Datenbindung zwischen den im adaptiven Formular und im JSON-Schema verfügbaren Feldern. Anschließend können Sie das adaptive Formular in eine Datenbank Ihrer Wahl integrieren, Daten in das Formular eintragen und dieses über das Formularportal an die Datenbank senden.

Die folgende Abbildung zeigt verschiedene Phasen der Integration eines konvertierten adaptiven Formulars in eine Datenbank mithilfe von Forms Portal:

![Datenbankintegration](assets/database_integration.gif)

Dieser Artikel gibt Anweisungen zu den einzelnen Schritten für die erfolgreiche Ausführung all dieser Integrationsstufen.

Das in diesem Artikel gezeigte Beispiel ist eine Referenzimplementierung benutzerdefinierter Daten- und Metadatendienste zur Integration einer Forms Portal-Seite in eine Datenbank. Die in der Beispielimplementierung verwendete Datenbank ist MySQL 5.6.24. Sie können die Forms Portal-Seite jedoch in jede Datenbank Ihrer Wahl integrieren.

## Voraussetzungen {#pre-requisites}

* Einrichten einer AEM 6.4- oder 6.5-Autoreninstanz
* Installieren Sie das [neueste Service Pack](https://helpx.adobe.com/experience-manager/aem-releases-updates.html) für Ihre AEM-Instanz
* Neueste Version des AEM Forms-Add-On-Pakets
* Configure [Automated Forms Conversion service](configure-service.md)
* Einrichten einer Datenbank. Die in der Beispielimplementierung verwendete Datenbank ist MySQL 5.6.24. Sie können das konvertierte adaptive Formular jedoch in jede beliebige Datenbank Ihrer Wahl integrieren.

## Verbindung zwischen der AEM-Instanz und der Datenbank einrichten{#set-up-connection-aem-instance-database}

Zur Einrichtung einer Verbindung zwischen einer AEM-Instanz und einer MYSQL-Datenbank gehören folgende Schritte:

* [Installation eines MYSQL-Connector-Pakets](#install-mysql-connector-java-file)

* [Schema und Tabellen in der Datenbank erstellen](#create-schema-and-tables-in-database)

* [Verbindungseinstellungen konfigurieren](#configure-connection-between-aem-instance-and-database)

* [Einrichten und Konfigurieren des Beispielpakets für die Forms Portal-Integration](#set-up-and-configure-sample)

### Installieren der Datei mysql-connector-java-5.1.39-bin.jar{#install-mysql-connector-java-file}

Führen Sie die folgenden Schritte auf allen Autoren- und Veröffentlichungsinstanzen aus, um die Datei mysql-connector-java-5.1.39-bin.jar zu installieren:

1. Navigieren Sie zu http://[server]:[port]/system/console/depfinder und suchen Sie nach dem com.mysql.jdbc-Paket.
1. Überprüfen Sie in der Spalte „Exportiert von“, ob das Paket von einem Paket exportiert wird. Fahren Sie fort, wenn das Paket nicht von einem Paket exportiert wird.
1. Navigate to http://[server]:[port]/system/console/bundles and click **[!UICONTROL Install/Update]**.
1. Click **[!UICONTROL Choose File]** and browse to select the mysql-connector-java-5.1.39-bin.jar file. Aktivieren **[!UICONTROL Start Bundle]** und **[!UICONTROL Refresh Packages]** aktivieren Sie außerdem die Kontrollkästchen.
1. Klicken Sie auf **[!UICONTROL Install]** oder **[!UICONTROL Update]**. Wenn dies abgeschlossen ist, starten Sie den Server neu.
1. (Nur Windows) Deaktivieren Sie die System-Firewall für Ihr Betriebssystem.

### Schema und Tabellen in der Datenbank erstellen{#create-schema-and-tables-in-database}

Führen Sie die folgenden Schritte aus, um ein Schema und Tabellen in der Datenbank zu erstellen:

1. Erstellen Sie ein Schema in der Datenbank mit der folgenden SQL-Anweisung:

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   wobei **formsportal** sich auf den Namen des Schemas bezieht.

1. Erstellen Sie mit der folgenden SQL-Anweisung eine Tabelle **data** im Datenbankschema:

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Erstellen Sie mit der folgenden SQL-Anweisung eine Tabelle **metadata** im Datenbankschema:

   ```sql
   CREATE TABLE `metadata` (
       `formPath` varchar(1000) DEFAULT NULL,
       `formType` varchar(100) DEFAULT NULL,
       `description` text,
       `formName` varchar(255) DEFAULT NULL,
       `owner` varchar(255) DEFAULT NULL,
       `enableAnonymousSave` varchar(45) DEFAULT NULL,
       `renderPath` varchar(1000) DEFAULT NULL,
       `nodeType` varchar(45) DEFAULT NULL,
       `charset` varchar(45) DEFAULT NULL,
       `userdataID` varchar(45) DEFAULT NULL,
       `status` varchar(45) DEFAULT NULL,
       `formmodel` varchar(45) DEFAULT NULL,
       `markedForDeletion` varchar(45) DEFAULT NULL,
       `showDorClass` varchar(255) DEFAULT NULL,
       `sling:resourceType` varchar(1000) DEFAULT NULL,
       `attachmentList` longtext,
       `draftID` varchar(45) DEFAULT NULL,
       `submitID` varchar(45) DEFAULT NULL,
       `id` varchar(60) NOT NULL,
       `profile` varchar(255) DEFAULT NULL,
       `submitUrl` varchar(1000) DEFAULT NULL,
       `xdpRef` varchar(1000) DEFAULT NULL,
       `agreementId` varchar(255) DEFAULT NULL,
       `nextSigners` varchar(255) DEFAULT NULL,
       `eSignStatus` varchar(45) DEFAULT NULL,
       `pendingSignID` varchar(45) DEFAULT NULL,
       `agreementDataId` varchar(255) DEFAULT NULL,
       `enablePortalSubmit` varchar(45) DEFAULT NULL,
       `submitType` varchar(45) DEFAULT NULL,
       `dataType` varchar(45) DEFAULT NULL,
       `jcr:lastModified` varchar(45) DEFAULT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `ID_UNIQUE` (`id`)
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Erstellen Sie mit der folgenden SQL-Anweisung eine Tabelle **additionalmetadatatable** im Datenbankschema:

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Erstellen Sie mit der folgenden SQL-Anweisung eine Tabelle **commenttable** im Datenbankschema:

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### Konfigurieren der Verbindung zwischen der AEM-Instanz und der Datenbank {#configure-connection-between-aem-instance-and-database}

Führen Sie die folgenden Konfigurationsschritte aus, um eine Verbindung zwischen der AEM-Instanz und der MYSQL-Datenbank herzustellen:

1. Go to AEM Web Console Configuration page at *http://[host]:[port]/system/console/configMgr*.
1. Klicken Sie auf , um **[!UICONTROL Forms Portal Draft and Submission Configuration]** im Bearbeitungsmodus zu öffnen.
1. Geben Sie die Werte für die Eigenschaften an, wie in der folgenden Tabelle beschrieben:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Eigenschaft</strong></th> 
    <th><strong>Beschreibung</strong></th>
    <th><strong>Wert</strong></th> 
    </tr> 
    <tr> 
    <td><p>Forms Portal-Datendienst für Entwurf</p></td> 
    <td><p>Bezeichner für den Datendienst für Entwurf</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal-Metadatendienst für Entwurf</p></td> 
    <td><p>Bezeichner für den Dienst für Entwurfs-Metadaten</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal-Datendienst für Übermittlung</p></td> 
    <td><p>Bezeichner für den Dienst zur Datenübermittlung</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal-Metadatendienst für Übermittlung</p></td> 
    <td><p>Bezeichner für den Dienst Metadatenübermittlung</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal ausstehender Sign Datendienst</p></td> 
    <td><p>Bezeichner für den Dienst für Daten zu ausstehende Signaturen</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal ausstehender Sign Metadatendienst</p></td> 
    <td><p>Bezeichner für den Dienst für Metadaten zu ausstehende Signaturen</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Leave other configurations as is and click **[!UICONTROL Save]**.
1. Find and click to open **[!UICONTROL Apache Sling Connection Pooled DataSource]** in edit mode in the Web Console Configuration. Geben Sie die Werte für die Eigenschaften an, wie in der folgenden Tabelle beschrieben:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Eigenschaft</strong></th> 
    <th><strong>Wert</strong></th> 
    </tr> 
    <tr> 
    <td><p>Datenquellenname</p></td> 
    <td><p>Ein Datenquellenname für das Filtern der Treiber aus dem Datenquellenpool. In der Beispielimplementierung wird Forms Portal als Datenquellenname verwendet.</p></td>
    </tr>
    <tr> 
    <td><p>JDBC-Treiberklasse</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>JDBC-Verbindungs-URI</p></td> 
    <td><p>jdbc:mysql://[host]:[port]/[schema_name]</p></td>
    </tr>
    <tr> 
    <td><p>Benutzername</p></td> 
    <td><p>Ein Benutzername zur Authentifizierung und zum Durchführen von Aktionen auf Datenbanktabellen</p></td>
    </tr>
    <tr> 
    <td><p>Kennwort</p></td> 
    <td><p>Kennwort für den Benutzernamen</p></td>
    </tr>
    <tr> 
    <td><p>Transaktions-Isolierung</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>Max. aktive Verbindungen</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>Max. inaktive Verbindungen</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>Min. inaktive Verbindungen</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Anfangsgröße</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Max. Wartezeit</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>Test zu Leihung</p></td> 
    <td><p>Aktiviert</p></td>
    </tr>
     <tr> 
    <td><p>Test bei inaktiv</p></td> 
    <td><p>Aktiviert</p></td>
    </tr>
     <tr> 
    <td><p>Validierungsanfrage</p></td> 
    <td><p>Beispielwerte sind SELECT 1 (mysql), select 1 von Dual (oracle), SELECT 1 (MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>Timeout für Validierungsanfrage</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

### Beispiel installieren und konfigurieren {#set-up-and-configure-sample}

Führen Sie die folgenden Schritte für alle Autoren- und Veröffentlichungsinstanzen durch, um das Beispiel zu installieren und zu konfigurieren:

1. Laden Sie das folgende **aem-fp-db-integration-sample-pkg-6.1.2.zip**-Paket auf Ihr Dateisystem herunter.

   [Datei laden](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Gehen Sie zu AEM Package Manager unter *http://[host]:[port]/crx/packmgr/*.
1. Klicken Sie auf **[!UICONTROL Upload Package]**.
1. Navigieren Sie zum Paket **aem-fp-db-integration-sample-pkg-6.1.2.zip**, wählen Sie es aus und klicken Sie auf **[!UICONTROL OK]**.
1. Click **[!UICONTROL Install]** next to the package to install the package.

## Konfigurieren des konvertierten adaptiven Formulars für die Integration von Forms Portal {#configure-converted-adaptive-form-for-forms-portal-integration}

Führen Sie die folgenden Schritte aus, um die Übermittlung des adaptiven Formulars über die Seite „Formularportal“ zu aktivieren:
1. [Führen Sie die Konvertierung aus](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process), um ein Quellformular in ein adaptives Formular zu konvertieren.
1. Öffnen Sie Ihr adaptives Formular im Bearbeitungsmodus.
1. Tippen Sie auf Formularcontainer und wählen Sie „Konfigurieren“ und dann ![Adaptives Formular konfigurieren](assets/configure-adaptive-form.png).
1. Wählen Sie im **[!UICONTROL Submission]** Abschnitt **[!UICONTROL Forms Portal Submit Action]** aus der **[!UICONTROL Submit Action]** Dropdown-Liste.
1. Tippen Sie auf ![Vorlagenrichtlinie speichern](assets/edit_template_done.png), um die Einstellungen zu speichern.

## Erstellen und Konfigurieren der Forms Portal-Seite {#create-configure-forms-portal-page}

Führen Sie die folgenden Schritte aus, um eine Forms Portal-Seite zu erstellen und zu konfigurieren, damit Sie über diese Seite adaptive Formulare senden können:

1. Log on to the AEM author instance and tap **[!UICONTROL Adobe Experience Manager]** >  **[!UICONTROL Sites]**.
1. Select the location where you want to save the new Forms Portal page and tap **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. Select the template for the page, tap **[!UICONTROL Next]**, specify a title for the page and tap **[!UICONTROL Create]**.
1. Tap **[!UICONTROL Edit]** to configure the page.
1. In the page header, tap ![Edit template](assets/edit_template_sites.png)  > **[!UICONTROL Edit Template]** to open the template of the page.
1. Tippen Sie auf Layout-Container und anschließend auf ![Vorlagenrichtlinie bearbeiten](assets/edit_template_policy.png). Aktivieren Sie auf der **[!UICONTROL Allowed Components]** Registerkarte die Optionen **[!UICONTROL Document Services]** und **[!UICONTROL Document Services Predicates]** und tippen Sie auf ![Vorlagenrichtlinie](assets/edit_template_done.png)speichern.
1. Insert **[!UICONTROL Search & Lister]** component in the page. Daraufhin werden alle in Ihrer AEM-Instanz verfügbaren adaptiven Formulare auf der Seite aufgelistet.
1. Insert **[!UICONTROL Drafts & Submissions]** component in the page. Auf der Forms Portal-Seite werden zwei Registerkarten **[!UICONTROL Draft Forms]** und **[!UICONTROL Submitted Forms]** angezeigt. The **[!UICONTROL Draft Forms]** tab also displays the converted adaptive form generated using the steps mentioned in [Configure the converted adaptive form for Forms Portal integration](#configure-converted-adaptive-form-for-forms-portal-integration)

1. Tap **[!UICONTROL Preview]**, tap the converted adaptive form, specify values for adaptive form fields and submit it. Die Werte, die Sie für adaptive Formularfelder angeben, werden an die integrierte Datenbank gesendet.
