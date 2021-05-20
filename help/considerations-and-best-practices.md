---
title: 'Best Practices und Hinweise '
description: NICHT VERÖFFENTLICHEN
seo-description: NICHT VERÖFFENTLICHEN
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
source-git-commit: b2d29c22a275f2dc6a82593cf5e441c8da0bba13
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 100%

---


# Best Practices und Überlegungen {#do-not-publish-best-practices-and-considerations}

<!--
[DO NOT PUBLISH]
-->

Der Dienst für die automatische Konvertierung von AEM Forms konvertiert ein PDF-Formular in ein adaptives Formular. Der Dienst verwendet künstliche Intelligenz und Algorithmen für maschinelles Lernen, um das Layout und die Felder des Quellformulars zu verstehen. Jeder auf maschinellem Lernen basierende Dienst lernt kontinuierlich aus den Quelldaten und liefert eine verbesserte Ausgabe. Diese Dienste lernen aus Erfahrung, genau wie Menschen.

Der Dienst zur automatischen Formularkonvertierung wird für eine Vielzahl von Formularen geschult. Er erkennt problemlos Felder in einem Quellformular und erzeugt adaptive Formulare. Es gibt jedoch einige Felder und Stile in PDF-Formularen, die für das menschliche Auge leicht sichtbar, für den Dienst jedoch schwer zu verstehen sind. Der Dienst weist einigen Feldern oder Stilen eventuell andere als die zutreffenden Feldtypen oder Bedienfelder zu. Alle diese Feld- und Stilmuster sind nachfolgend aufgeführt.

Der Dienst beginnt, diese Muster zu erkennen und ihnen die richtigen Felder oder Bedienfelder zuzuweisen, da er weiterhin aus den Quelldaten lernt. Derzeit können Sie den Editor [Überprüfen und Korrigieren](review-correct-ui-edited.md) verwenden, um solche Probleme zu beheben. Machen Sie sich mit [adaptiven Formularkomponenten](https://helpx.adobe.com/de/experience-manager/6-5/forms/using/introduction-forms-authoring.html) vertraut, bevor Sie mit der Behebung der Probleme beginnen oder weiterlesen.

## Allgemein {#general}

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Bekannte Muster und Auflösung</td> 
   <td width="70%">Beispiel</td> 
  </tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst konvertiert keine ausgefüllten PDF-Formulare in adaptive Formulare.</p> <p> </p> <p><strong>Lösung</strong></p> <p>Verwenden Sie leere adaptive Formulare.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst kann Text und Felder möglicherweise nicht erkennen, wenn sie im Formular zu dicht beieinander stehen.</p> <p> </p> <p><strong>Lösung</strong></p> <p>Vergrößern Sie den Abstand zwischen Text und Feldern eines dichten Formulars, bevor Sie mit der Konvertierung beginnen.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst unterstützt keine gescannten Formulare.</p> <p> </p> <p><strong>Lösung</strong></p> <p>Verwenden Sie keine gescannten Formulare. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst extrahiert keine Bilder und Texte in Bildern. </p> <p> </p> <p><strong>Lösung</strong></p> <p>Fügen Sie konvertierten Formularen manuell Bilder oder Text hinzu.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Tabellen mit gepunkteten oder unklaren Grenzen und Rahmen werden nicht konvertiert.</p> <p><strong>Lösung</strong></p> <p>Verwenden Sie Tabellen mit klaren expliziten Grenzen und Rahmen.  </p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## Auswahlgruppe  {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Muster</td> 
   <td width="70%">Beispiel</td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Auswahlgruppenoptionen mit anderen Formen als Kästchen oder Kreis werden nicht in entsprechende adaptive Formularkomponenten konvertiert. </p> <p> </p> <p><strong>Lösung</strong></p> <p>Ändern Sie die Formen der Auswahloptionen in ein Kästchen oder einen Kreis, oder verwenden Sie den Editor „Überprüfen und Korrigieren“, um die Formen zu identifizieren.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## Formularfelder {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Muster</td> 
   <td width="70%">Beispiel</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>Muster</strong></p> <p>Der Dienst identifiziert keine Felder ohne klare Rahmen.</p> <p> </p> <p><strong>Lösung</strong></p> <p>Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Felder zu identifizieren.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst lässt einige Formularfelder mit Bildunterschriften unten oder rechts unerkannt.</p> <p> </p> <p><strong>Lösung</strong></p> <p>Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Felder zu identifizieren</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst führt einige Formularfelder zusammen oder weist ihnen einen falschen Typ zu, wenn sie sehr nahe beieinander liegen oder keine klaren Grenzen haben. </p> <p> </p> <p><strong>Lösung</strong></p> <p>Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Felder zu identifizieren.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst kann Felder mit weit entfernten Beschriftungen oder einer gepunkteten Linie zwischen Beschriftung und Eingabefeld möglicherweise nicht erkennen.</p> <p> </p> <p><strong>Lösung</strong></p> <p>Verwenden Sie Formularfelder mit klaren Grenzen oder verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Probleme zu beheben.</p> </td> 
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
   <td><p><strong>Muster</strong></p> <p>Listen mit Formularfeldern werden zusammengeführt oder nicht in entsprechende adaptive Formularkomponenten konvertiert</p> <p><strong>Lösung</strong></p> <p>Verwenden Sie Formularfelder mit klaren Grenzen oder verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Probleme zu beheben.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst kann einige verschachtelte Listen nicht identifizieren</p> <p> </p> <p><strong>Lösung</strong></p> <p>Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Probleme zu beheben.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>Muster</strong></p> <p>Der Dienst führt einige Listen mit Auswahlgruppen miteinander zusammen</p> <p><strong>Lösung</strong></p> <p>Verwenden Sie den Editor „Überprüfen und Korrigieren“, um solche Probleme zu beheben.</p> </td> 
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

