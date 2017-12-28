---
title: Neues, altes Theme
author: David Henning
type: post
date: 2012-02-29T21:40:30+00:00
url: /2012/02/neues-altes-theme.html
dsq_thread_id:
  - 594538249

---
Gerade eben habe ich auf ein neues Theme umgestellt. Das Design bleibt gleich, aber die Technik dahinter habe ich komplett ausgetauscht. Zuletzt war das Theme &#8222;Platform PagesLines&#8220; im Einsatz. Einerseits ist es sehr umfangreich ausgestattet und bietet extrem viele Konfigurationsmöglichkeiten. Damit einher kommen aber ein völlig überladener, tief verschachtelter Quelltext und ein recht großer PHP-Part, da viele Seitenteile durch zig Funktionen und Klassen erzeugt werden. Die Entscheidung das Theme neu zu schreiben viel mir daher nicht sonderlich schwer.

Wie es sich heutzutage gehört, ist das Markup sehr flach gehalten und setzt auf [HTML 5][1]. Um die Stylesheets schneller und effizienter zu entwickeln, setze ich auf das CSS-Framework [Compass][2]. Dessen Grundlage ist das Framework [SASS][3], das die Style-Schreiberei durch mögliche Verschachtelungen, Variablen, Berechnungen, Vererbung, Style-Templates (Mixins) deutlich vereinfacht. Dazu schreibt man einfach die Styles im SCSS-Format und SASS bzw. Compass erstellen aus daraus eine voll einsatzfähige CSS-Datei &#8212; auf Wunsch schon komplett minified bzw. compressed.

Jedem, der viel mit CSS arbeitet, kann ich nur unbedingt empfehlen, sich Compass näher anzuschauen. Selbst nach nur kurzer Einarbeitung spart man sich enorm viel Arbeit und kann auch spätere Änderungen deutlich schneller vornehmen, besonders wenn es um Selektor-Gruppen geht.

Für die Zukunft plane ich weitere Optimierungen, u.A. den Einsatz von [ControlJS][4], das JavaScripts asynchron lädt und erst nach Rendern des DOMs ausführt. Zusätzlich möchte ich an die Anzahl der HTTP-Requests pro Seitenanruf auf ein absolutes Minimum reduzieren.

Ziel des Ganzen ist, wie schon auch der Einsatz von [Amazon CloudFront][5] als [CDN][6] und [memcached][7], ein kleines, hoch performantes Spielzeug zu haben. Übung darin schadet nie, denn Ladezeiten haben einen sehr großen Einfluss darauf, ob ein Besucher bleibt oder nicht. Dazu plane in nächster Zeit auch einige Beiträge zu Strategien, Ladezeiten zu optimieren bzw. entsprechende Tutorials.

[Als kleines Schmankerl stelle ich das Theme mit allen notwendigen Dateien in ein öffentliches Github-Repository.][8]

 [1]: http://dev.w3.org/html5/spec/Overview.html
 [2]: http://compass-style.org/
 [3]: http://sass-lang.com/
 [4]: http://stevesouders.com/controljs/
 [5]: http://aws.amazon.com/de/cloudfront/
 [6]: http://de.wikipedia.org/wiki/Content_Distribution_Network
 [7]: http://memcached.org/
 [8]: https://github.com/MadCatme/mcw-blue