---
title: Spaß mit jQuery
author: David Henning
type: post
date: 2008-06-19T00:35:18+00:00
url: /2008/06/spas-mit-jquery.html

---
Das letzte meiner [jQuery-Beispiele][1] beschäftigt sich ja damit, externen Links ein Icon und target=&#8220;_blank&#8220; zu verpassen. Mit allem drum und dran umfasst die Funktion zehn Zeilen Code. Dank ein paar Tricks und der wunderbaren CSS-Selektor-Syntax, geht das ganze aber auch in einer einzigen Zeile:

<pre name="code" class="js">$('#content .post a:not([href^="' + $('base').attr('href') + '"])[href^="http://"]').css('background', 'url(' + templateURL + 'img/shape_move_forwards.png) no-repeat right 1px').css('padding-right', '20px').attr('title', 'Externer Link').attr('target', '_blank');</pre>

Es werden also alle a-Element der Klasse &#8222;post&#8220; innerhalb der ID &#8222;content&#8220; angewählt, die nicht mit der Basis-URL, aber dafür mit &#8222;http://&#8220; beginnen. So wird sichergestellt, dass alle externen Links erwischt werden, aber z.B. relative interne Links (die [TinyMCE][2] gerne macht) oder ID-Aufrufe nicht betroffen sind.

Allen betroffenen Elementen wird nun das Icon als Hintergrundbild zugewiesen, ein entsprechendes Padding gesetzt, sowie das title- und target-Attribut.

Mit einer so effizienten und gleichzeitig einfachten Syntax zu arbeiten, macht einfach Spaß. Und so lange diese CSS-Selektoren noch nicht vollständig implementiert sind, hilft jQuery browser-unabhängig aus.

 [1]: 2008/06/jquery-beispiele.html
 [2]: http://tinymce.moxiecode.com/