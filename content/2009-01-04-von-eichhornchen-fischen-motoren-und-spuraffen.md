---
title: Von Eichhörnchen-Fischen, Motoren und Spuraffen
author: David Henning
type: post
date: 2009-01-04T00:49:14+00:00
url: /2009/01/von-eichhornchen-fischen-motoren-und-spuraffen.html
dsq_thread_id:
  - 506667951

---
<pre></pre>

Oder anders gesagt: Benchmarks von Squirrelfish, V8 und Tracemonkey mit Hilfe von [dromaeo.com][1].

Testsystem: Intel Core 2 Duo P8600, 2 GB RAM), MacOS X 10.5.6 (MacBook Pro 15&#8243; 2,4 GHz Late 2008)

![Ergebnisse (Mac)][2]

<pre></pre>

Testystem: Intel Core 2 Duo E8400, 2 GB RAM, Windows XP Service Pack 3

![Ergebnisse (PC)][3]

Das Squirrelfish schnell ist, war ja schon bekannt. Aber das es V8 und Tracemonkey dermaßen in den Hintern tritt, hätte ich nicht gedacht. Auf die Antwort von Mozilla und Google dürfen wir alle gespannt sein.

Anmerkung zum Internet Explorer: leider konnte ich weder den IE 6 noch 7 dazu bewegen, überhaupt einen Benchmark durchlaufen zu lassen. Entweder meldete er Javascript-Fehler oder stürzte ab. Aus Tests von anderen Leuten, ist aber bekannt, dass er im Vergleich extrem langsam ist &#8211; im Schnitt etwa 10 &#8211; 15 Sekunden.

Während bei Safari der Taktenraten- und Cache-Unterschied sich noch halbwegs realistisch in den Ergebissen von OS X und Windows widerspiegelt, zeigt sich bei Firefox, dass Mozilla die Mac-Version noch weiter optimieren sollte.

**Update:** Nun mit Diagrammen statt Text-Ergebnissen.

 [1]: http://dromaeo.com/
 [2]: https://www.madcatswelt.org/wp-content/uploads/2009-01-04_mac.png "Ergebnisse (Mac)"
 [3]: https://www.madcatswelt.org/wp-content/uploads/2009-01-04_pc.png "Ergebnisse (PC)"