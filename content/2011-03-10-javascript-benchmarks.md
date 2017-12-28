---
title: JavaScript-Benchmarks
author: David Henning
type: post
date: 2011-03-09T22:06:42+00:00
url: /2011/03/javascript-benchmarks.html
dsq_thread_id:
  - 468168477

---
In den letzten Monaten tat sich viel in der Browser-Landschaft: Mitte Dezember kam Opera 11. Google bringt fast schon im Monatstakt neue Chrome-Versionen &#8212; erst gestern Version 10. Wie Microsoft heute mitteilte, kommt der finale Internet Explorer 9 am 14. März und Firefox 4 wird auch nicht mehr lange auf sich warten lassen. Es wird wieder Zeit, sich einen Überblick in Sachen JavaScript-Leistung zu verschaffen. Inbesondere Google und Opera treiben hier die Entwicklung stark voran, während Mozilla und Microsoft versuchen endlich aufzuschließen.

Als Testplattform diente ein Intel Core i5 750 mit 8 GB RAM, einer Intel X25-M G2 80 GB und Windows 7 Professional x64 SP1.

Hier die Ergebnisse als Diagramme:

<img class="alignnone size-full wp-image-715" title="benchmarks_2011-03-09" src="https://www.madcatswelt.org/wp-content/uploads/benchmarks_2011-03-09.png" alt="" srcset="https://www.madcatswelt.org/wp-content/uploads/benchmarks_2011-03-09.png 576w, https://www.madcatswelt.org/wp-content/uploads/benchmarks_2011-03-09-241x300.png 241w" sizes="(max-width: 576px) 100vw, 576px" />

Aufgrund der Charakteristik und Optimierungen der einzelnen Benchmarks, gibt es keinen klaren Sieger. Am neutralsten &#8212; obwohl er dem WebKit-Projekt entstammt &#8212; erscheint mir SunSpider. Es ist dabei fast schon ironisch, dass die eigene Engine &#8222;Nitro&#8220; am schlechsten abschneidet.

Im Vergleich zu den anderen Ergebnissen, sind die Einzelwerte aber recht nahe beisammen. Verwunderlich ist nur, dass der Internet Explorer 9 selbst Chrome und Opera leicht abhängt. Hier wurde ja desöfteren schon eine SunSpider-Optimierung der Engine seitens Microsoft vermutet. Belegen lässt sich das allerdings nicht. Klar ist aber, dass die JavaScript-Leistung gegenüber den Vorgängern deutlich zugenommen hat.

Bei den V8-Benchmarks ist klar ersichtlich, dass er für Chrome optimiert wurde, während der Rest des Feldes grob auf einem Niveau zu sein scheint. Ähnlich drastisch scheint Kraken auf die Tracer-Technik von TraceMonkey bzw. JägerMonkey (Mozilla) ausgerichtet zu sein. Die Tracing-Technik dominierte oft Tests, wenn sie aufgrund des Programmierung des Scripts richtig arbeiten kann. In der Praxis ist das ist leider selten der Fall, daher kam meist der herkömliche JIT in Mozillas SpiderMonkey Engine zum Einsatz. Ab Firefox 4 steht ein neuer JIT namens JaegerMonkey zur Verfügung, der zum Teil auf WebKits Nitro basiert und deutliche Vorteile gegenüber dem alten System hat.

**Fazit**

Ingesamt überzeugt Chrome 10 bzw. V8 mit der besten Gesamtleistung im Starterfeld. Opera 11, Firefox 4 und der Internet Explorer 9 teilen sich das Mittelfeld, wobei Opera 11 die Gruppe klar anführt und der IE 9 das Rücklicht hält. Safari 5 schneidet in zwei von drei Tests als Letzter und im dritten als Vorletzter ab. Hier sollten Apple die und anderen Initiatoren des WebKit-Projekts demnächst nachlegen, sonst wird der einstmalige ICE schnell zum Regionalzug.

Wie bei solchen Benchmarks üblich, handelt es sich hierbei natürlich in erster Linie um theoretische Ergebnisse. Praktisch betrachtet, also beim normalen Surfen, sind die Unterschiede der Testkandidaten bei weitem nicht so drastisch. Heftige Ausreißer wie noch zwischen Firefox 3.6 oder dem IE 8 und aktuellen Chrome-Versionen entfallen fast vollständig. Mozillas und Microsofts Anstrengungen wieder Anschluss zu finden, sind also geglückt.