---
title: Schnellere Websites mit RequireJS
author: David Henning
type: post
date: 2012-03-24T21:47:56+00:00
url: /2012/03/schnellere-websites-mit-require-js.html
dsq_thread_id:
  - 623144150

---
Mit diesem Eintrag beginnt meine kleine Serie über schnellere Websites. Im Rahmen dieser Reihe werde ich Strategien und praktische Maßnahmen vorstellen, um die Ladegeschwindigkeiten zu analysieren, Schwachpunkte zu finden und zu vermeiden.

### Warum RequireJS?

In den meisten Programmiersprachen existieren Funktionen wie require(), #include oder import, um weitere Bestandteile eines Programms aus einer Datei bzw. eines Namespaces zu laden. In JavaScript gibt es solche Möglichkeiten bislang nicht. [RequireJS][1] beseitigt dieses Problem. JavaScript-Dateien werden durch RequireJS asynchron nachgeladen, so dass mehrere Dateien parallel abgeholt werden können. Gleichzeitig ist es dadurch möglich, auf script-Element im Quelltext zu verzichten und damit das Rendern der Seite zu beschleunigen.

Script-Elemente sind Blocker im Rendering-Prozess. Browser arbeiten den Quelltext einer Seite von oben nach unten durch. Wenn ein script-Element auftaucht, muss es erst ausgeführt werden, bevor der Browser sich um den nachfolgenden Quelltext kümmern kann. Externe JavaScripts können aus diesem Grund massiven Einfluss auf die Ladegeschwindigkeit einer Seite haben, auch wenn die eigentliche Website schon längst vom Web-Server an den Browser ausgeliefert wurde.

Falls ein externes Script auf einem langsamen Server liegt, muss der Browser warten, bis er es komplett abgerufen und ausgeführt hat. Sollte das aufgerufene Script gar nicht mehr vorhanden sein, wartet der Browser seine Timeout-Einstellung ab, bis er weitermacht. Sicherlich hat jeder schon mal gesehen, dass eine Website nur bis einem gewissen Teil angezeigt wird und erst nach ein paar Sekunden der Rest dargestellt wird. Mit sehr hoher Wahrscheinlichkeit, war dies ein nicht mehr vorhandenes oder nur sehr langsam ladendes JavaScript.

Asynchrones Abholen findet erst nach dem Rendern der Seite statt und blockiert daher nichts. Dazu lässt sich bei konsequentem Nutzen von RequireJS der Einsatz von script-Elementen weitgehend vermeiden. Im Idealfall gibt es nur noch ein script-Element, das RequireJS lädt und ein weiteres Script startet, um die gesamte JavaScript-Funktionalität einer Seite zu initialisieren.

<!--more-->

### Konfiguration

Hier ein simples Beispiel einer Require-JS-Konfiguration mit jQuery:

<pre class="javascript">(function() {
    require.config({
        paths: {
            'jquery': 'libs/jquery/jquery-1.7.1'
        }
    });

    require(['jquery'], function(jQuery){
      jQuery.noConflict();
    });
})();</pre>

Zuerst wird RequireJS so konfiguriert, dass [jQuery][2] mittels des Keywords &#8222;jquery&#8220; geladen werden kann. Im Konfigurations-Objekt &#8222;paths&#8220; wird dafür als Attributsname &#8222;jquery&#8220; und als Wert der Pfad (ausgehend vom Verzeichnis des Scripts) zu jQuery gesetzt. Anschließend wird require() aufgerufen und als erster Parameter wird ein Array mit den aufzulösenden Abhängigkeiten erwartet &#8212; hier jQuery. Man kann hier ein unter &#8222;paths&#8220; gesetztes Keyword, den Pfad oder auch externe JavaScripts über die URL angeben. Falls es sich um ein Modul handelt, wird auf die Dateiendung &#8222;.js&#8220; verzichtet.

Im zweiten Parameter wird eine Callback-Funktion definiert, deren Aufruf unmittelbar nach dem Laden der Abhängikeiten stattfindet. Als Parameter folgen hier die Rückgaben der angeforderten JavaScript-Dateien. In diesem Fall ist es ein jQuery-Objekt, das sogleich in den No-Conflict-Modus versetzt wird, um nicht mit evtl. anderen geladenen Bibliotheken zu kollidieren. Dieses Verfahren ist besser bekannt als [Dependency Injection][3].

### Module

RequireJS bietet über die Modul-Definition eine elegante Lösung, Programmbestandteile zu kapseln und Abhängigkeiten (z.B. jQuery) aufzulösen. Aktuell setze ich hier drei Module ein, die Funktionen für einzelne Beiträge (Syntax Highlighting, Lightbox etc.) übernehmen sowie das Tracking über Piwik bzw. Google Analytics starten.

Alle Module sind so aufgebaut, dass sie Abhängigkeiten in Form von Bibliotheken oder anderen Modulen erst auflösen, wenn sie gebraucht werden. Gleichzeitig stellt RequireJS sicher, dass eine Abhängikeit nur einmal geladen wird und für jedes andere Modul zur Verfügung steht.

Ein Beispiel-Modul:

<pre class="javascript">define(['jquery'], function($) {
    var exports = {};

    exports.init = function() {
        $('body').append('&lt;h1&gt;Hello World!&lt;/h1&gt;');
    }

    return exports;
});</pre>

Mit define() wird die Moduldefinition gestartet. Anschließend passiert das gleiche, wie in der Funktion require(). Zuerst werden die Abhängigkeiten als Array definiert, danach startet eine Dependecy Injection in die Callback-Funktion. An dieser Stelle wird ein Dollarzeichen als Parameter für die Abhängigkeit verwendet, um jQuery wie gewohnt einsetzen zu können. Anschließend wird das Objekt &#8222;exports&#8220; mit der Methode init() erstellt und zurückgegeben. Wird das Modul an anderer Stelle über require() geladen und das exports-Objekt in die Callback-Funktion injiziert, kann man in ihr die init-Methode aufrufen und damit das Modul starten. Natürlich es ist aber auch möglich, darauf zu verzichten und innerhalb der Modul-Callback-Funktion direkt Code auszuführen.

Um ein Modul an anderer Stelle mit require() zu laden, gibt man den Pfad, ausgehend vom Verzeichnis der RequireJS-Konfiguration, zum Modul an. Wie vorhin schon beschrieben, muss man hierbei auf die Dateiendung &#8222;.js&#8220; verzichten.

Zu guter letzt muss RequireJS selbst samt Konfiguration geladen werden:

<pre class="html">&lt;script src="js/libs/require/require.js" data-main="js/config"&gt;&lt;/script&gt;</pre>

Ein simples Script-Element hierzu genügt &#8212; am besten unmittelbar vor dem schließenden body-Element. Zusätzlich wird mit dem Daten-Attribut &#8222;main&#8220; noch der Pfad zur Konfiguration mitgegeben. RequireJS bindet das entsprechende JavaScript automatisch ein und startet sie.

### Fazit

RequireJS ist ein mächtiges Tool, das alleine schon durch die Kapselung in verschiedene Module dem Entwickler sehr viele Vorteile bringt. Durch die immer größer werdende Komplexität von Web-Sites bzw. Web-Applikationen sind andere Formen der Organisation notwendig geworden, die in anderen Programmiersprachen schon von Anfang an vorhanden waren.

Dank der Module mit ihren von RequireJS automatisch aufgelösten Abhängigkeiten durch Dependency Injection, lassen sich schnell und einfach, neue Funktionalitäten in eine Website implementieren, ohne weitere script-Elemente in den HTML-Quelltext einfügen zu müssen.

Bis auf RequireJS selbst werden alle definierten Abhängigkeiten bzw. Module asynchron geladen, ohne das Rendern der Seite zu blockieren. Da Browser asynchrone Anfragen parallel abarbeiten können, werden insgesamt alle Scripts schneller geladen und früher ausgeführt, als es bei einer traditionellen Verwendung von JavaScript möglich wäre.

Das Ergebnis ist ein großer Vorteil für alle Beteiligten. Für den Nutzer wird eine Website mit viel JavaScript deutlich schneller dargestellt, während die Funktionalitäten im Hintergrund nachgeladen werden, ohne dass man etwas davon bemerkt. Aus Sicht der Entwickler bietet RequireJS eine elegante Möglichkeit, schnelle neue Funktionen zu entwickeln, Abhängigkeiten einfach aufzulösen und durch die Module strukturierter zu arbeiten.

Abgesehen von TypeKit und Disqus laufen alle JavaScript-Bestandteile dieser Seite als Modul. Zwar lässt sich TypeKit problemlos als Modul umsetzen, nur werden die Schriften erst nach dem Rendern der Seite geladen. Für etwa eine halbe Sekunde sind die Fallback-Schriften zu sehen, erst dann die über TypeKit-Schriften dargestellt. Da das nicht Sinn und Zweck von TypeKit und Euch Leser irritiert, wird TypeKit klassisch im head-Element vor den Stylesheets geladen.

Disqus ist dagegen als WordPress-Plug-In eingebunden und darauf würde ich auch nur sehr ungern verzichten. Ich könnte das Plug-In zwar anpassen, aber damit wäre die Update-Fähigkeit dahin. Da Disqus seine Scripts selbst asynchron lädt, sehe ich auch keine Notwendigkeit, den ganzen Aufwand zu betreiben und Module zu schreiben. Allerdings habe ich andere Plug-Ins wie die Lightbox und das Syntax Highlighting rausgeworfen und durch RequireJS-Module ersetzt, die nun fester Bestandteil des Themes sind. Geladen werden sie aber nur, wenn auch Beiträge vorhanden sind, die eine der Funktionen brauchen.

Falls ich Euch Interesse zu RequireJS geweckt habe, könnt Ihr meine Implementierung inkl. eine Ladesystems für Module aus dem HTML-Quelltext heraus im [GitHub-Repository meines WordPress-Themes][4] anschauen oder auch einen Fork erstellen, um damit selbst entwickeln zu können. Falls jemand Ideen oder Verbesserungen hat, ich freue mich über jede Anregung und jeden Pull-Request in GitHub.

 [1]: http://requirejs.org/
 [2]: http://jquery.com/
 [3]: http://de.wikipedia.org/wiki/Dependency_Injection
 [4]: https://github.com/MadCatme/mcw-blue