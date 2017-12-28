---
title: Google Chrome
author: David Henning
type: post
date: 2008-09-05T19:40:20+00:00
url: /2008/09/google-chrome.html
dsq_thread_id:
  - 467743929

---
Die Katze ist nun seit ein paar Tagen aus dem Sack und ich kann das dauernde Lamentieren über Datenschutz und Spionage nicht mehr hören. Bei einem Open Source-Projekt ist so eine Diskussion überflüssig. Jeder kann sich den Quelltext herunterladen und prüfen. Google Suggest in der Adressleiste lässt sich abschalten und die Browser-ID ebenso umgehen &#8211; letztere nutzt übrigens auch Mozilla Firefox beim Auto-Update &#8230;

Leider geht die technische Seite in diesem Theater etwas unter. Dabei ist gerade das doch die Stärke von Chrome. Eine virtuelle Maschine (im Sinne einer Java-VM) für Javascript, die dazu keinen Bytecode, sondern gleich x86-Code generiert, hat massive Geschwindigkeitsvorteile und ist durch Einkapselung auch noch sicherer. Zumindest solange keine schwerwiegenden Fehler auftreten, die es erlauben ins eigentliche Betriebssystem einzudringen.

Letztendlich wird es aber zur Philosophiefrage werden, ob man nun einen normalen Interpreter oder eine kompilierende VM benutzt. Als reiner Interpreter wird Tracemonkey in Firefox 3.1 wohl gleich auf liegen. Allerdings sind Tracemonkey, Squirrelfisch und V8 noch neu, so ist sicher noch viel Luft nach oben.

Dass die Wahl der Render Engine dagegen auf Webkit fiel, ist schon etwas verwunderlich. Schließlich ist Google der Hauptgeldgeber der Mozilla Foundation und es bleibt die Frage: warum nicht Gecko? Als Grund wurden die guten Erfahrungen mit Webkit während der Entwicklung von Android und geringer Ressourcenhunger angeführt.

Soweit so richtig, aber ich glaube eher, dass Mozilla nicht dem Tempo folgen kann, welches Google vorschwebt und man sich daher gegen Gecko entschiedt. Neue Firefox- und Thunderbird-Versionen verzögern sich meist gewaltig. Bei den anderen Projekten wie z.B. Sunbird, sieht es auch nicht besser aus.

Chrome soll offensichtlich ein schneller Schlag gegen Microsoft bzw. den Internet Explorer werden. Aus meiner Sicht als beruflicher Web-Entwickler, kann ich das nur befürworten. Die Jungs aus den Redmond müssen endlich ganz aus ihrem Dornröschenschlaf aufwachen. Zwar hat sie Firefox geweckt, aber noch taumeln sie schlaftrunken durch die Gegend.

Nach fünf Jahren absolutem Stillstand (2001 &#8211; 2006) und auch dem IE 7, muss endlich mehr passieren. Version 8 ist ein richtiger Schritt, aber Microsoft hat sicher mehr Möglichkeiten, als mehr schlecht als recht mit Gecko, Presto und Webkit gleichziehen zu können. Wir mussten und müssen uns in der Branche immer noch mit den Hinterlassenschaften dieser technischen Stagnation rumschlagen. Das kann und darf so nicht mehr weitergehen.

Darum wünsche ich Google viel Erfolg, auch wenn ich vorerst bei Firefox bleiben werde. Es gibt einfach zu viele Extensions, die inzwischen unverzichtbar geworden sind &#8211; zumindest für uns Entwickler.