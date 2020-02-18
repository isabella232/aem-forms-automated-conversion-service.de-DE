---
title: '[KEINE VERÖFFENTLICHUNG] Bewährte Verfahren und Überlegungen '
seo-title: '[KEINE VERÖFFENTLICHUNG] Bewährte Verfahren und Überlegungen '
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
translation-type: tm+mt
source-git-commit: afe461baa5bcfc1106c16aae2d6a9c839ea675e8

---


# [Best Practices und Überlegungen] NICHT VERÖFFENTLICHEN {#do-not-publish-best-practices-and-considerations}

Der AEM Forms-Dienst für die automatische Konvertierung konvertiert ein PDF-Formular in ein adaptives Formular. Der Dienst verwendet Algorithmen für künstliche Intelligenz und maschinelles Lernen, um das Layout und die Felder des Quellformulars zu verstehen. Jeder maschinelle Lerndienst lernt ständig aus den Quelldaten und erzeugt mit jeder Kehrtwende eine verbesserte Ausgabe. Diese Dienste lernen von Erfahrungen wie Menschen.

Der Dienst für die automatisierte Formularkonvertierung wird für eine große Anzahl von Formularen geschult. Es identifiziert einfach Felder in einem Quellformular und erzeugt adaptive Formulare. Es gibt jedoch einige Felder und Stile in PDF-Formularen, die für das menschliche Auge leicht sichtbar, aber für den Dienst schwer zu verstehen sind. Der Dienst kann bestimmten Feldern oder Stilen unterschiedliche Feldtypen oder Bereiche zuweisen. Alle diese Felder- und Stilmuster sind unten aufgeführt.

Der Dienst würde beginnen, diese Muster zu identifizieren und ihnen korrekte Felder oder Bereiche zuzuweisen, da er weiterhin aus den Quelldaten lernt. Vorläufig können Sie diese Probleme mit dem Editor &quot; [Überprüfen&quot;und &quot;Korrigieren](review-correct-ui-edited.md) &quot;beheben. Bevor Sie mit der Behebung der Probleme beginnen oder weitere Informationen lesen, sollten Sie sich mit den [adaptiven Formularkomponenten](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)vertraut machen.

## Allgemein {#general}

<!--
Comment Type: draft

<ul>
<li>Service does not convert filled PDF forms to adaptive form. Use empty adaptive forms.Service does not convert colored PDF forms to adaptive form. Use black and white or grayscale adaptive forms. <br /> </li>
<li>Service does not convert filled PDF forms to adaptive form. Use empty adaptive forms.</li>
<li>Service does not support scanned forms. Do not use scanned forms. </li>
<li>Service can fail to recognize text and fields in a dense form. Increase the width between text and fields of a dense form before starting the conversion.</li>
<li>Service does not extract images. Manually add images to converted forms.</li>
<li>Service does not extract text present within an image. Manually add text to the adaptive form.</li>
</ul>
-->

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Bekannte Muster und Auflösung</td> 
   <td width="70%">Beispiel</td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Dienst konvertiert keine farbigen PDF-Formulare in adaptive Formulare.</p> <p> </p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie PDF-Formulare in Schwarzweiß oder Graustufen. </p> </td> 
   <td style="text-align: left;"> <img src="assets/coloured-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Dienst konvertiert keine ausgefüllten PDF-Formulare in adaptive Formulare.</p> <p> </p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie leere adaptive Formulare.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst erkennt Text und Felder in einem dichten Formular möglicherweise nicht.</p> <p> </p> <p><strong>Auflösung</strong></p> <p>Erhöhen Sie die Breite zwischen Text und Feldern eines dichten Formulars, bevor Sie mit der Konvertierung beginnen.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Dienst unterstützt keine gescannten Formulare.</p> <p> </p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie keine gescannten Formulare. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst extrahiert keine Bilder und Text in Bildern. </p> <p> </p> <p><strong>Auflösung</strong></p> <p>Fügen Sie den konvertierten Formularen manuell Bilder oder Text hinzu.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Tabellen mit gepunkteten oder nicht klaren Grenzen und Rahmen werden nicht konvertiert.</p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie Tabellen mit klaren und eindeutigen Begrenzungen. unterstützt.</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## Auswahlgruppe {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Muster</td> 
   <td width="70%">Beispiel</td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Auswahlgruppenoptionen mit anderen Formen als "Feld"oder "Kreis"werden nicht in entsprechende adaptive Formularkomponenten konvertiert. </p> <p> </p> <p><strong>Auflösung</strong></p> <p>Ändern Sie die Auswahl der Optionen in Form eines Felds oder Kreises oder verwenden Sie den Editor zum Überprüfen und Korrigieren, um die Formen zu identifizieren.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## Form fields {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Muster</td> 
   <td width="70%">Beispiel</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>Muster</strong></p> <p>Der Dienst identifiziert keine Felder ohne klare Grenzen.</p> <p> </p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie den Editor zum Überprüfen und Korrigieren, um solche Felder zu identifizieren.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst lässt einige Formularfelder mit Beschriftungen unten oder rechts unidentifiziert.</p> <p> </p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie den Editor "Überprüfen"und "Korrigieren", um solche Felder zu identifizieren.</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst führt einen falschen Typ zu bestimmten Formularfeldern zusammen oder weist diese zu, die sehr nahe beieinander platziert sind oder keine klaren Ränder haben. </p> <p> </p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie den Editor zum Überprüfen und Korrigieren, um solche Felder zu identifizieren.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst kann Felder mit weit entfernten Beschriftungen oder einer gepunkteten Linie zwischen dem Beschriftungs- und dem Eingabefeld nicht erkennen.</p> <p> </p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie Formularfelder mit klaren Begrenzungen oder verwenden Sie den Editor zum Überprüfen und Korrigieren, um diese Probleme zu beheben.</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## Listen {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Muster</td> 
   <td width="70%">Beispiel</td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Listen mit Formularfeldern werden zusammengeführt oder nicht in entsprechende adaptive Formularkomponenten konvertiert</p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie Formularfelder mit klaren Begrenzungen oder verwenden Sie den Editor zum Überprüfen und Korrigieren, um diese Probleme zu beheben.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Dienst kann einige verschachtelte Listen unidentifiziert lassen</p> <p> </p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie den Editor zum Überprüfen und Korrigieren, um diese Probleme zu beheben.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Dienst führt einige Listen zusammen, die Auswahlgruppen enthalten</p> <p><strong>Auflösung</strong></p> <p>Verwenden Sie den Editor zum Überprüfen und Korrigieren, um diese Probleme zu beheben.</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

