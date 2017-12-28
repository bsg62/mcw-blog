---
title: jQuery-Beispiele
author: David Henning
type: post
date: 2008-06-15T22:00:00+00:00
url: /2008/06/jquery-beispiele.html
dsq_thread_id:
  - 467743978

---
Es gibt zwar viele Javascript-Frameworks, aber sowohl privat als auch im Büro bevorzuge ich [jQuery][1]. Mit knapp 31 KB (gepackt) ist es schön klein, nicht überladen und inzwischen auch recht flott. Der größte Vorteil ist aber, dass der Zugriff auf die DOM-Objekte über die CSS-Syntax erfolgt &#8211; und auch mit den Selektoren, die z.B. der Internet Explorer nicht unterstützt.

Anhand von ein paar Code-Zeilen, die ich hier im Blog verwende, wird klar wie simpel, aber auch mächtig jQuery ist.

Grundsätzlich befinden sich alle Funktionen in der jQuery-Methode ready(), die auf das gesamte DOM angewandt wird. Dabei werden die Elemente schon manipuilert, sobald der DOM-Baum fertig geladen ist und nicht erst, wie beim Event onload(), wenn alles geladen wurde.

<pre name="code" class="js">$(document).ready(function() {<br />	Code &#8230;<br />});<br /></pre>

jQuery bietet ein eigenes Event-Handling an, das es über die CSS-Syntax ermöglicht Events an DOM-Elemente zu hängen. Als Beispiel fungiert hier das Abschicken eines Textfeldes beim Druck auf Enter.

<pre name="code" class="js">$('form input[type="text"]').keyup(function(event) {<br />	if(event.keyCode == 13) {<br />		$(this).parents('form').submit();<br />	}<br />});<br /></pre>

Damit wird an jedes Textfeld das Event keyup() gebunden und beim Druck auf Enter das übergeordnete Formular abgeschickt.

Als zweites Beispiel dient die automatische Erkennung, ob ein Link innerhalb eines Blog-Eintrags auf eine externe Seite verweist und falls ja, automatisch das Attribut target auf &#8222;_blank&#8220; gesetzt wird, sowie dem a-Elemet ein Bild für eine entsprechende Kennzeichnung als externer Link anhängt wird.

<pre name="code" class="js">$('#content .post a').each(function() {<br />	if($(this).attr('href').indexOf($('base').attr('href')) == -1 <br />		 && $(this).attr('href') != '#' && $(this).children('img').length == 0 <br />		 && $(this).attr('href').indexOf('javascript:') == -1) {<br />		<br />		$(this).attr('title', 'Externer Link').attr('target', '_blank');<br />		$(this).after(' <a title="Externer Link" href="' + $(this).attr('href') + '" target="_blank"><img style="vertical-align: middle;" src="' + templateURL + 'img/shape_move_forwards.png" alt="External link" /></a>');<br />	}<br />});<br /></pre>

&#8222;$(this)&#8220; steht für aktuelle Element des each-Durchlaufs. Es handelt sich dabei aber um ein jQuery-Objekt, das z.B. nicht alle DOM-Methoden erlaubt. In einer each-Schleife ist aber auch der Zugriff auf das DOM-Element über &#8222;this&#8220; möglich.

Die If-Bedingung prüft, ob die verlinkte URL zur eigenen Seite gehört, ob sie einen Anker-Aufruf enthält oder Javascript-Code ausführt. Trifft nichts von dem zu, werden die Attribute &#8222;title&#8220; und &#8222;target&#8220; gesetzt. Solche Verkettungen sind möglich, weil jede manipulierende jQuery-Methode eine Referenz auf das bearbeitete Objekt zurückgibt. Danach wird dem a-Element ein weiteres a anhängt, das die Bild-Kennzeichnung für einen externen Link enthält.

Zu guter letzt noch ein Einzeiler, der ein Problem mit dem Syntax Highlighter löst. Aus Kompatibilitätsgründen zu älteren Einträgen bin ich leider gezwungen, jeden Text durch die PHP-Funktion nl2br() zu schicken, um Zeilenumbrüche in br-Elemente ersetzen zu lassen. Bei Code-Ausschnitten in pre-Elementen ergibt sich dabei ein Problem, weil entweder das br-Element als Text am jeder Zeile anzeigt wird oder sogar umgebrochen wird und somit zig überflüssige Leerzeilen vorhanden sind.

<pre name="code" class="js">$('pre[name="code"] br').remove();</pre>

Damit werden alle br-Elemente entfernt und die Code-Ansicht ist sauber. Sicherlich hätte man das ganze auch gleich serverseitig lösen können, aber wozu sich mit regulären Ausdrücken rumquälen, wenn eine Zeile Javascript ausreicht?

Ich hoffe, dass meine Beispiele halbwegs verständlich sind und der ein oder andere, sich entschließt jQuery eine Chance zu geben &#8211; es lohnt sich!

 [1]: http://jquery.com/