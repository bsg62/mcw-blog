---
title: Aktuelle JavaScript-Benchmarks
author: David Henning
type: post
date: 2011-11-05T21:52:49+00:00
url: /2011/11/aktuelle-javascript-benchmarks.html
dsq_thread_id:
  - 467749298

---
Nach etwas über einem halben Jahr wird es wieder einmal Zeit, den JavaScript Engines der aktuellen Browser-Versionen auf den Zahn zu fühlen. Die Versionssprünge im Vergleich zu den [letzten Benchmarks][1] sind beachtlich. Firefox ging von Version 3 (4 war noch Beta) auf 7, Chrome von 10 auf 15. Microsoft machte da einen vergleichsweise kleinen Schritt von 8 auf 9, während Apple und Opera bei ihren Hauptversionen 5 und 11 treu geblieben sind.

Wie üblich dient als Testplattform mein Privatrechner mit folgender Spezifikation: Intel Core i5 750, 8 GB RAM, Intel X25 G2 80 GB und Windows 7 Professional x64 SP 1.

Hier sind die Ergebnisse:

<img class="aligncenter size-full wp-image-798" title="js_benchmarks_v4_1" src="https://www.madcatswelt.org/wp-content/uploads/js_benchmarks_v4_1.png" alt="" srcset="https://www.madcatswelt.org/wp-content/uploads/js_benchmarks_v4_1.png 548w, https://www.madcatswelt.org/wp-content/uploads/js_benchmarks_v4_1-227x300.png 227w" sizes="(max-width: 548px) 100vw, 548px" />

&nbsp;

Es gibt auch dieses mal keinen klaren Gewinner, der sich alle drei Siege sichern konnte, aber Chrome 15 ist im Schnitt wieder die Nummer 1. Der Internet Explorer 9 mag zwar unter SunSpider der schnellste Kandidat sein, er verliert jedoch die anderen zwei Tests klar. Es liegt daher die Vermutung nahe, dass Microsoft hier einige Optimierungen vorgenommen hat &#8212; zumal sich an SunSpider schon länger nichts mehr getan hat.

Wie man schön sehen kann, hat Apple im letzten halben Jahr wirklich Fortschritte mit der Nitro Engine gemacht. Safari hat sich von der roten Laterne ins Mittelfeld vorgekämpft und überholt nun Firefox in gleich zwei Disziplinen. Es bleibt abzuwarten, ob Apple den Vorsprung halten kann. Ab Firefox 9 wird Mozillas [JIT][2] JägerMonkey durch [Type Inference][3] bis zu 30% mehr Leistung bringen. Dazu befindet sich mit [IonMonkey][4] ein neuer JIT in Arbeit, der wahrscheinlich JägerMonkey und evtl. auch TraceMonkey ersetzen wird. IonMonkey wird eine andere, moderne Architektur besitzen und damit die Wartbarkeit als auch Optimierungsmöglichkeiten für die Entwickler deutlich verbessern.

Bleibt noch Opera 11, der sich mal wieder sehr gut schlägt und die klare Nummer Zwei im Starterfeld ist.

### Fazit

Chrome gewinnt &#8212; wie immer. Opera ist Zweiter und im weiteren Feld kämpft sich Safari an Firefox und Microsofts Internet Explorer vorbei.

Ich bin gespannt, ob Microsoft mit dem Internet Explorer 10 wieder aufholen kann. Vielleicht sollte man in Redmond auch die Release-Zyklen überdenken. Alle anderen Hersteller können wesentlich schneller reagieren und optimieren, während Microsoft nur jährlich neue Major Releases bringen will. Wobei ich es für fraglich halte, ob wirklich jedes Jahr eine neue Version kommen wird.

Natürlich haben theoretische Benchmarks in der Praxis weit weniger Relevanz. Meine aktuellen Experimente mit [ExtJS][5] zeigen sehr deutlich, dass bei [Rich Internet Applications][6] Firefox immer noch kein sonderlich gutes Bild abgibt. Das aufgebaute UI, das für eine RIA eh noch recht spartanisch ausgestattet ist, läuft in allen anderen Browsern wesentlich weniger träge und ruckelig. Gleiches lässt sich auf diverse andere JavaScript-lastige Seiten übertragen, z.B. GMail oder iCloud.

JägerMonkey mit Type Inference, IonMonkey und die lang erwartete Integration des [Electrolysis-Projekts][7] sind darum wichtiger denn je.

 [1]: https://www.madcatswelt.org/2011/03/javascript-benchmarks.html
 [2]: http://de.wikipedia.org/wiki/Just-in-time-Kompilierung
 [3]: http://en.wikipedia.org/wiki/Type_inference
 [4]: https://wiki.mozilla.org/Platform/Features/IonMonkey
 [5]: http://www.sencha.com/products/extjs/
 [6]: http://de.wikipedia.org/wiki/Rich_Internet_Application
 [7]: https://wiki.mozilla.org/Electrolysis