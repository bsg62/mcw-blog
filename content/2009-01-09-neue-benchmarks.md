---
title: Neue Benchmarks
author: David Henning
type: post
date: 2009-01-09T19:10:50+00:00
url: /2009/01/neue-benchmarks.html

---
Dromaeo hat vor kurzem ein neues Testverfahren eingeführt. Statt der benötigten Zeit für die Tests, wird nun gemessen, wie viele Durchläufe durchschnittlich pro Sekunde in einer fest definierten Zeit erreicht werden. Das macht die ganze Sache langwieriger, aber auch genauer und sagt wesentlich mehr über die Leistungsfähigkeit einer Javascript Engine aus.

Statt auf zwei unterschiedlichen Systemen zu messen, habe ich nun unterschiedliche Benchmarks gewählt: Dromaeo Javascript Test (Mozilla.org), SunSpider Javascript Test (Webkit-Team) und V8 Javascript Test (Google).

![Testergebnisse][1]

Testsystem: Intel Core 2 Duo E8400, 2 GB RAM, Windows XP SP 3

Ein Bild sagt mehr als 1.000 Worte. Chrome deklassiert alle anderen Browser, nur im hauseigenen V8-Test ist das aktuelle Webkit Nightly Build einen Tick schneller. Wie üblich sind die Entwickler-Versionen ihren aktuellen Final-Kollegen deutlich voraus, und die Javascript-Leistung des Internet Explorers, sofern er sich überhaupt testen lies, ist ein schlechter Scherz.

Ein blamables Ergebnis für Microsoft, das mit dem IE 8 auch nicht großartig besser werden wird. Wenn man sich in Redmond angesichts solcher vernichtenden Benchmarks nicht endlich im Zugzwang sieht, sind sie entweder blind und/oder blöd. Google treibt die Entwicklung mit großen Schritten voran, während nur Webkit bzw. Apple halbwegs mithalten kann. Mozilla.org und Opera müssen sich sehr anstrengen, um wieder Anschluss zu finden.

Und Microsoft? Tja, ich sehe nur zwei Möglichkeiten: den ganzen alten IE-Quellcode öffentlich verbrennen und komplett neu schreiben, oder man setzt in Zukunft auf Webkit/Squirrelfish bzw. Webkit/V8 oder Gecko/Tracemonkey.

 [1]: https://www.madcatswelt.org/images/2009-01-09.png