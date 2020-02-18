---
title: Dokument aus Datensatz während der Konvertierung erstellen
seo-title: Dokument aus Datensatz während der Konvertierung erstellen
description: Empfohlene Pfade zum Generieren eines DoR basierend auf dem Typ der für die Konvertierung verwendeten Quellformulare.
seo-description: Empfohlene Pfade zum Generieren eines DoR basierend auf dem Typ der für die Konvertierung verwendeten Quellformulare.
page-status-flag: never-activated
uuid: 7f0f5bf3-21be-449a-b23e-5946a9fd7ed4
contentOwner: khsingh
discoiquuid: 75f6e6bc-7636-4b40-919c-8b20a6ccbb1f
translation-type: tm+mt
source-git-commit: 640d72d7961ef0c2393bf0ae6745d918e388a056

---


# Empfohlene Arbeitsabläufe zur Aktivierung der Datensatzgenerierung für adaptive Formulare {#recommended-workflows-dor-generation}

Das Datensatzdokument (DoR) ermöglicht es Ihnen, die von Ihnen bereitgestellten Informationen aufzuzeichnen und sie in einem adaptiven Formular zu senden, sodass Sie später darauf verweisen können.
Das DoR verwendet eine Basisvorlage, um das Layout zu definieren. Sie können ein DoR entweder mit einer Standardvorlage oder mit einer anderen Vorlage mit dem adaptiven Formular erstellen.

![Generiertes Datensatzdokument](assets/document_of_record.gif)

Weitere Informationen zum Generieren eines DoR finden Sie unter Datensatzdokument [generieren für adaptive Formulare](https://helpx.adobe.com/experience-manager/6-5/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.html).

Der [Automatisierte Formularkonvertierungsdienst](../help/introduction.md) konvertiert die folgenden Quellformulare in adaptive Formulare:

* nicht interaktive PDF-Formulare
* Acro Forms
* XFA-basierte PDF-Formulare

Basierend auf dem Quellformular, das Sie für die Konvertierung verwenden, können Sie ein DoR generieren, indem Sie:

* eine Standardvorlage
* Quellformular als Vorlage: Wenn Sie diese Option auswählen, verknüpft der Konvertierungsdienst das Quellformular automatisch mit dem konvertierten adaptiven Formular als DoR-Vorlage.
* Verknüpfen einer anderen Vorlage mit dem konvertierten adaptiven Formular

Die folgende Tabelle zeigt ein Beispiel dafür, wie sich die von Ihnen verwendete DoR-Vorlage auf das Layout des generierten DoR auswirkt:

<table> 
 <tbody>
 <tr>
  <td><p><strong>Quellformular</strong></p></td>
  <td><p><strong>Generiertes DoR</strong></p></td> 
   </tr>
  <tr>
   <td><img src="assets/source_xdp_updated.png"/></td>
   <td><p>Wenn Sie die Standardvorlage zum Generieren von DoR verwenden:</br><img src="assets/source_form_default_updated.png"/></td>
   </tr>
   <tr>
   <td></td>
   <td><p>Wenn Sie das Quellformular als Vorlage zum Generieren von DoR verwenden:</br></p><img src="assets/source_form_dor_updated.png"/></td>
   </tr>
  </tbody>
</table>

Wie in der Tabelle dargestellt, behält das DoR das Layout des Quellformulars bei, wenn Sie das Quellformular als Vorlage verwenden.
In diesem Artikel werden die empfohlenen Pfade zum Generieren eines DoR basierend auf den drei Typen von Quellformularen beschrieben.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Quellformular</strong></th> 
   <th><strong>Methoden zum Generieren von DoR</strong></th> 
  </tr> 
  <tr> 
   <td><p>Nicht interaktive PDF-Formulare</p></td> 
   <td> 
    <ul> 
     <li><a href="#generate-document-of-record-using-cloud-configuration">DoR-Generierung vor der Konvertierung adaptiver Formulare aktivieren, um DoR mit einer Standardvorlage zu generieren</a></li> 
     <li><a href="#edit-adaptive-form-properties-generate-document-of-record">Bearbeiten Sie die Eigenschaften adaptiver Formulare nach der Konvertierung adaptiver Formulare, um die DoR-Generierung mit einer Standard- oder einer anderen Formularvorlage zu aktivieren.</a></li> 
    </ul> </td> 
  </tr>
  <tr> 
   <td><p>Acro Forms oder XFA-basierte PDF-Formulare</p></td> 
   <td> 
    <ul> 
     <li><a href="#use-input-form-as-template-to-generate-document-of-record">DoR-Generierung vor der Konvertierung adaptiver Formulare aktivieren, um DoR mithilfe des Quellformulars als Vorlage zu generieren</a></li> 
     <li><a href="#edit-adaptive-form-properties-to-generate-document-of-record">Bearbeiten Sie die Eigenschaften adaptiver Formulare nach der Konvertierung des adaptiven Formulars, um die DoR-Generierung mithilfe der Standardvorlage, des Quellformulars als Vorlage oder einer anderen Formularvorlage zu aktivieren.</a></li> 
    </ul> </td> 
  </tr>    
 </tbody> 
</table>

## Datensatzdokument für nicht interaktive PDF-Formulare erstellen {#generate-document-of-record-non-interactive-pdf}

Wenn Sie ein nicht interaktives PDF-Formular als Quellformular für den automatisierten Forms-Konvertierungsdienst verwenden, haben Sie folgende Möglichkeiten:

* entweder DoR-Generierung vor der Konvertierung adaptiver Formulare aktivieren, um DoR mit einer Standardvorlage zu generieren
* oder bearbeiten Sie nach der Konvertierung des adaptiven Formulars die Eigenschaften des adaptiven Formulars, um die DoR-Generierung mit einer Standard- oder einer anderen Formularvorlage zu aktivieren

### DoR-Generierung vor Konvertierung aktivieren, um DoR mit Standardvorlage zu generieren {#generate-document-of-record-using-cloud-configuration}

1. Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > Eigenschaften der für die Konvertierung verwendeten Cloud-Konfiguration > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** -Option.

   ![Datensatzdokument mit Cloud-Konfiguration erstellen](assets/generate_dor_cloud_config.gif)

1. Tap **[!UICONTROL Save & Close]** to save the settings.

1. [Führen Sie die Konversion](../help/convert-existing-forms-to-adaptive-forms.md)aus. Stellen Sie sicher, dass Sie die in Schritt 1 dieser Anweisungen bearbeitete Cloud-Konfiguration verwenden.
Beim Senden des konvertierten adaptiven Formulars wird das DoR automatisch mit der Standardvorlage generiert.

### Bearbeiten Sie die Eigenschaften adaptiver Formulare nach der Konvertierung, um die DoR-Generierung zu aktivieren {#edit-adaptive-form-properties-generate-document-of-record}

Wenn Sie die DoR-Generierung nicht aktivieren, bevor Sie das Quellformular in ein adaptives Formular konvertieren, können Sie dies auch nach der Konvertierung tun.

1. [Führen Sie die Konvertierung](../help/convert-existing-forms-to-adaptive-forms.md) auf dem nicht interaktiven PDF-Formular aus, um ein adaptives Formular zu generieren.

1. Wählen Sie das adaptive Formular im **[!UICONTROL output]** Ordner aus und tippen Sie auf **[!UICONTROL Properties]**.

1. Erweitern Sie auf der **[!UICONTROL Form Model]** Registerkarte den **[!UICONTROL Document of Record Template Configuration]** Abschnitt und wählen Sie **[!UICONTROL Generate Document of Record]**.

   ![Generieren von Dokument aus Datensatz](assets/generate_dor_af_properties.png)

1. Tap **[!UICONTROL Save & Close]** to save the settings.

Beim Senden des konvertierten adaptiven Formulars wird das DoR automatisch mit der Standardvorlage generiert. Wenn Sie eine andere DoR-Vorlage mit dem konvertierten adaptiven Formular verknüpfen möchten, können Sie die **[!UICONTROL Associate form template as the Document of Record template]** Option auswählen.

## Datensatzdokument für Acro Forms oder XFA-basierte PDF-Formulare erstellen {#generate-document-of-record-acroform-xfaform}

Wenn Sie ein Acro-Formular oder ein XFA-basiertes PDF-Formular als Quellformular für den automatisierten Forms-Konvertierungsdienst verwenden, können Sie:

* entweder DoR-Generierung vor der Konvertierung des adaptiven Formulars aktivieren, um DoR mithilfe des Quellformulars als Vorlage zu generieren

* oder bearbeiten Sie nach der Konvertierung des adaptiven Formulars die Eigenschaften des adaptiven Formulars, um die DoR-Generierung mithilfe der Standardvorlage, des Quellformulars als Vorlage oder einer anderen Formularvorlage zu aktivieren

### DoR-Generierung vor Konvertierung aktivieren, um DoR mithilfe der Quellformularvorlage zu generieren {#use-input-form-as-template-to-generate-document-of-record}

1. Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > Eigenschaften der für die Konvertierung verwendeten Cloud-Konfiguration > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** -Option.

1. Tap **[!UICONTROL Save & Close]** to save the settings.

1. [Führen Sie die Konversion](../help/convert-existing-forms-to-adaptive-forms.md)aus. Stellen Sie sicher, dass Sie die in Schritt 1 dieser Anweisungen bearbeitete Cloud-Konfiguration verwenden.
Der Konvertierungsdienst verknüpft das Acro-Formular oder das XFA-basierte PDF-Formular automatisch mit dem konvertierten adaptiven Formular als DoR-Vorlage.
Sie können die Eigenschaften des adaptiven Formulars öffnen, um die DoR-Vorlage im **[!UICONTROL Document of Record Template Configuration]** Abschnitt der **[!UICONTROL Form Model]** Registerkarte anzuzeigen.

   ![Eigenschaften von adaptiven Formularen bearbeiten, um Datensatzdokument zu erstellen](assets/generate_dor_af_properties_xdp_acro.png)

   Beim Senden des konvertierten adaptiven Formulars wird das DoR automatisch mit der Vorlage des Quellformulars generiert.

### Bearbeiten Sie die Eigenschaften adaptiver Formulare nach der Konvertierung, um die DoR-Generierung zu aktivieren {#edit-adaptive-form-properties-to-generate-document-of-record}

1. [Führen Sie die Konvertierung](../help/convert-existing-forms-to-adaptive-forms.md) auf dem nicht interaktiven PDF-Formular aus, um ein adaptives Formular zu generieren.

1. Wählen Sie das adaptive Formular im **[!UICONTROL output]** Ordner aus und tippen Sie auf **[!UICONTROL Properties]**.

1. Erweitern Sie auf der **[!UICONTROL Form Model]** Registerkarte den **[!UICONTROL Document of Record Template Configuration]** Abschnitt und wählen Sie **[!UICONTROL Generate Document of Record]** die Option, um die DoR-Generierung mithilfe der Standardvorlage zu aktivieren.
Sie können auch die **[!UICONTROL Associate form template as the Document of Record template]** Option auswählen und die Vorlage auswählen, um die DoR-Generierung mithilfe der Quellformularvorlage oder einer anderen Formularvorlage zu aktivieren.

1. Tap **[!UICONTROL Save & Close]** to save the settings.
