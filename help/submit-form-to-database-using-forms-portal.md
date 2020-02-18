---
title: Übermitteln adaptiver Formulare in die Datenbank mithilfe von Forms Portal
description: Erweitern Sie das Standard-Metadatenmodell, um für Ihr Unternehmen spezifische Muster, Überprüfungen und Entitäten hinzuzufügen und Konfigurationen auf adaptive Formularfelder anzuwenden, während der Dienst für die automatisierte Formularkonvertierung ausgeführt wird.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: 040b0ddb489b5bdfd640a93b22cd7bc512a39aea

---


# Adaptive Formulare mit Datenbank mithilfe von Forms Portal integrieren {#submit-forms-to-database-using-forms-portal}

Der Dienst &quot;Automatisierte Formularkonvertierung&quot;ermöglicht die Konvertierung eines nicht interaktiven PDF-Formulars, eines Acro-Formulars oder eines XFA-basierten PDF-Formulars in ein adaptives Formular. Beim Starten des Konvertierungsprozesses haben Sie die Möglichkeit, ein adaptives Formular entweder mit oder ohne Datenbindungen zu erstellen.

Wenn Sie ein adaptives Formular ohne Datenbindungen erstellen möchten, können Sie das konvertierte adaptive Formular nach der Konvertierung in ein Formulardatenmodell, ein XML-Schema oder ein JSON-Schema integrieren. Wenn Sie jedoch ein adaptives Formular mit Datenbindungen generieren, verknüpft der Konvertierungsdienst automatisch die adaptiven Formulare mit einem JSON-Schema und erstellt eine Datenbindung zwischen den im adaptiven Formular verfügbaren Feldern und dem JSON-Schema. Anschließend können Sie das adaptive Formular in eine Datenbank Ihrer Wahl integrieren, Daten im Formular ausfüllen und es mit Forms Portal an die Datenbank senden.

Die folgende Abbildung zeigt die verschiedenen Phasen der Integration eines konvertierten adaptiven Formulars mit einer Datenbank mithilfe von Forms Portal:

![Datenbankintegration](assets/database_integration.gif)

In diesem Artikel werden die schrittweisen Anweisungen zum erfolgreichen Ausführen aller dieser Integrationsschritte beschrieben.

Das in diesem Artikel beschriebene Beispiel ist eine Referenzimplementierung benutzerdefinierter Daten- und Metadatendienste zum Integrieren einer Forms Portal-Seite in eine Datenbank. Die bei der Beispielimplementierung verwendete Datenbank ist MySQL 5.6.24. Sie können jedoch die Forms Portal-Seite in eine beliebige Datenbank Ihrer Wahl integrieren.

## Voraussetzungen {#pre-requisites}

* AEM 6.5 Autoreninstanz mit dem neuesten AEM 6.5 Service Pack
* Neueste Version des Add-On-Pakets für AEM Forms
* [Automatisierter Forms-Konvertierungsdienst](configure-service.md)
* Eine Datenbank, in die integriert werden soll. Die bei der Beispielimplementierung verwendete Datenbank ist MySQL 5.6.24. Sie können Forms Portal jedoch in eine beliebige Datenbank Ihrer Wahl integrieren.

## Verbindung zwischen AEM-Instanz und Datenbank einrichten {#set-up-connection-aem-instance-database}

Das Einrichten einer Verbindung zwischen einer AEM-Instanz und einer MYSQL-Datenbank besteht aus:

* [Installieren eines MYSQL-Connector-Pakets](#install-mysql-connector-java-file)

* [Schema und Tabellen in der Datenbank erstellen](#create-schema-and-tables-in-database)

* [Verbindungseinstellungen konfigurieren](#configure-connection-between-aem-instance-and-database)

* [Einrichten und Konfigurieren des Musterpakets für die Forms Portal-Integration](#set-up-and-configure-sample)

### Istallieren Sie mysql-connector-java-5.1.39-bin.jar file {#install-mysql-connector-java-file}

Führen Sie die folgenden Schritte auf allen Autor- und Veröffentlichungsinstanzen aus, um die Datei mysql-connector-java-5.1.39-bin.jar zu installieren:

1. Navigate to http://[server]:[port]/system/console/depfinder and search for com.mysql.jdbc package.
1. Überprüfen Sie in der Spalte „Exportiert von“, ob das Paket von einem Paket exportiert wird. Fahren Sie fort, wenn das Paket nicht von einem Paket exportiert wird.
1. Navigate to http://[server]:[port]/system/console/bundles and click **[!UICONTROL Install/Update]**.
1. Click **[!UICONTROL Choose File]** and browse to select the mysql-connector-java-5.1.39-bin.jar file. Wählen Sie außerdem **[!UICONTROL Start Bundle]** und **[!UICONTROL Refresh Packages]** Kontrollkästchen aus.
1. Klicken Sie auf **[!UICONTROL Install]** oder **[!UICONTROL Update]**. Wenn Sie bereit sind, starten Sie den Server neu.
1. (Nur Windows) Schalten Sie die System-Firewall für Ihr Betriebssystem aus.

### Schema und Tabellen in der Datenbank erstellen {#create-schema-and-tables-in-database}

Führen Sie die folgenden Schritte aus, um Schema und Tabellen in der Datenbank zu erstellen:

1. Erstellen Sie ein Schema in der Datenbank mit der folgenden SQL-Anweisung:

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   wobei **formsportal** auf den Namen des Schemas verweist.

1. Erstellen Sie mithilfe der folgenden SQL-Anweisung eine **Datentabelle** im Datenbankschema:

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Erstellen Sie mithilfe der folgenden SQL-Anweisung eine **Metadatentabelle** im Datenbankschema:

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

1. Erstellen Sie mithilfe der folgenden SQL-Anweisung eine **zusätzliche** Tabelle im Datenbankschema:

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Erstellen Sie mithilfe der folgenden SQL-Anweisung eine **kommenttable** Tabelle im Datenbankschema:

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### Verbindung zwischen AEM-Instanz und Datenbank konfigurieren {#configure-connection-between-aem-instance-and-database}

Führen Sie die folgenden Konfigurationsschritte aus, um eine Verbindung zwischen der AEM-Instanz und der MYSQL-Datenbank zu erstellen:

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
    <td><p>Bezeichner für den Metadatendienst für Entwurf</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal-Datendienst für Übermittlung</p></td> 
    <td><p>Bezeichner für den Datendienst für Übermittlung</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal-Metadatendienst für Übermittlung</p></td> 
    <td><p>Bezeichner für den Metadatendienst für Übermittlung</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal ausstehender Sign Datendienst</p></td> 
    <td><p>Bezeichner für ausstehenden Sign-Datendienst</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal ausstehender Sign Metadatendienst</p></td> 
    <td><p>Bezeichner für ausstehenden Sign Metadatendienst</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Leave other configurations as is and click **[!UICONTROL Save]**.
1. Klicken Sie auf und suchen Sie **[!UICONTROL Apache Sling Connection Pooled DataSource]** im Bearbeitungsmodus in der Web-Konsolenkonfiguration. Geben Sie die Werte für die Eigenschaften an, wie in der folgenden Tabelle beschrieben:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Eigenschaft</strong></th> 
    <th><strong>Wert</strong></th> 
    </tr> 
    <tr> 
    <td><p>Datenquellenname</p></td> 
    <td><p>Ein Datenquellenname für das Filtern der Treiber aus dem Datenquellenpool. Bei der Beispielimplementierung wird FormsPortal als Datenquellenname verwendet.</p></td>
    </tr>
    <tr> 
    <td><p>JDBC-Treiberklasse</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>JDBC-Verbindungs-URI</p></td> 
    <td><p>jdbc:mysql://[Host]:[Anschluss]/[Schemaname]</p></td>
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

Führen Sie die folgenden Schritte für alle Autoren- und Veröffentlichungsinstanzen aus, um das Beispiel zu installieren und zu konfigurieren:

1. Laden Sie das folgende **aem-fp-db-integration-sample-pkg-6.1.2.zip**-Paket auf Ihr Dateisystem herunter.

   [Datei laden](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Go to AEM package manager at *http://[host]:[port]/crx/packmgr/*.
1. Klicken Sie auf **[!UICONTROL Upload Package]**.
1. Wählen Sie das **aem-fp-db-integration-sample-pkg-6.1.2.zip**-Paket und klicken Sie auf **[!UICONTROL OK]**.
1. Click **[!UICONTROL Install]** next to the package to install the package.

## Konfigurieren des konvertierten adaptiven Formulars für die Forms Portal-Integration {#configure-converted-adaptive-form-for-forms-portal-integration}

Führen Sie die folgenden Schritte aus, um die Übermittlung adaptiver Formulare über die Forms Portal-Seite zu aktivieren:
1. [Führen Sie die Konvertierung](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) aus, um ein Quellformular in ein adaptives Formular zu konvertieren.
1. Öffnen Sie Ihr adaptives Formular im Bearbeitungsmodus.
1. Tippen Sie auf Formularcontainer und wählen Sie Adaptives Formular ![konfigurieren](assets/configure-adaptive-form.png).
1. Wählen Sie im **[!UICONTROL Submission]** Abschnitt **[!UICONTROL Forms Portal Submit Action]** aus der **[!UICONTROL Submit Action]** Dropdownliste aus.
1. Tippen Sie auf ![Vorlagenrichtlinie](assets/edit_template_done.png) speichern, um die Einstellungen zu speichern.

## Forms Portal-Seite erstellen und konfigurieren {#create-configure-forms-portal-page}

Führen Sie die folgenden Schritte aus, um eine Forms Portal-Seite zu erstellen und diese zu konfigurieren, damit Sie adaptive Formulare mit dieser Seite senden können:

1. Melden Sie sich bei der AEM-Autoreninstanz an und tippen Sie auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Sites]**.
1. Wählen Sie den Speicherort, an dem Sie die neue Forms Portal-Seite speichern möchten, und tippen Sie auf **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. Wählen Sie die Vorlage für die Seite aus, tippen Sie auf **[!UICONTROL Next]**, geben Sie einen Titel für die Seite an und tippen Sie auf **[!UICONTROL Create]**.
1. Tippen Sie auf , **[!UICONTROL Edit]** um die Seite zu konfigurieren.
1. Tippen Sie in der Kopfzeile der Seite auf Vorlage ![bearbeiten](assets/edit_template_sites.png) > **[!UICONTROL Edit Template]** , um die Vorlage der Seite zu öffnen.
1. Tippen Sie auf Layout-Container und dann auf ![Vorlagenrichtlinie](assets/edit_template_policy.png)bearbeiten. Aktivieren Sie auf der **[!UICONTROL Allowed Components]** Registerkarte die Optionen **[!UICONTROL Document Services]** und **[!UICONTROL Document Services Predicates]** und tippen Sie auf ![Vorlagenrichtlinie](assets/edit_template_done.png)speichern.
1. Komponente **[!UICONTROL Search & Lister]** in die Seite einfügen. Daher werden alle vorhandenen adaptiven Formulare, die in Ihrer AEM-Instanz verfügbar sind, auf der Seite aufgelistet.
1. Komponente **[!UICONTROL Drafts & Submissions]** in die Seite einfügen. Auf der Forms Portal-Seite werden zwei Registerkarten **[!UICONTROL Draft Forms]** und **[!UICONTROL Submitted Forms]** angezeigt. Auf der **[!UICONTROL Draft Forms]** [Registerkarte wird auch das konvertierte adaptive Formular angezeigt, das mit den unter Konfigurieren des konvertierten adaptiven Formulars für die Forms Portal-Integration beschriebenen Schritten generiert wurde](#configure-converted-adaptive-form-for-forms-portal-integration)

1. Tippen Sie auf **[!UICONTROL Preview]**, tippen Sie auf das konvertierte adaptive Formular, geben Sie Werte für adaptive Formularfelder an und senden Sie es. Die Werte, die Sie für adaptive Formularfelder angeben, werden an die integrierte Datenbank gesendet.
