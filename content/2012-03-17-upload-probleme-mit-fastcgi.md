---
title: Upload-Probleme mit FastCGI
author: David Henning
type: post
date: 2012-03-17T16:07:57+00:00
url: /2012/03/upload-probleme-mit-fastcgi.html
dsq_thread_id:
  - 614550436

---
Als ich eben die neue Galerie hochladen wollte, begrüßte mich bei jedem Versuch ein HTTP 500, besser bekannt als Internal Server Error. Die Meldung ist absolut nichtssagend und es lässt nur über Log-Dateien rausfinden, was eigentlich passiert.

Das Problem besteht offenbar seit dem Umzug auf einen virtuellen Server bei [Host Europe][1] mit Ubuntu 10.04 LTS und Plesk zur Verwaltung. In Plesk wird PHP standardmäßig via mod_php in den Apache eingebunden. Da das aber u.U. Rechteprobleme zwischen dem Apache-User und dem FTP-User bei von PHP angelegten Dateien geben kann, lasse ich PHP via FastCGI laufen. Das braucht zwar mehr RAM, hat aber den Vorteil, dass der PHP-Prozess und FTP-Zugang über den gleichen Nutzer laufen. Im Gegensatz zu suPHP funktionieren damit auch Opcode Caches wie APC und es muss nicht für jede Anfrage auf ein Script ein neuer PHP-Prozess gestartet werden.

Nach etwas Recherche, war die Ursache aber schnell klar. Um mit FastCGI arbeiten zu können, verwendet der Apache das Modul mod_fcgid, das folgenden Fehler auslöst:

<pre name="code" class="php">mod_fcgid: HTTP request length 1019250 (so far) exceeds MaxRequestLen (131072)
</pre>

Sprich: sämtliche HTTP-Anfragen, deren Länge mehr als 128 KB beträgt, werden durch FastCGI nicht zugelassen. Wie man sieht, war der Request knapp 1 MB groß, was bei größeren Bildern in ordentlicher Qualität schnell passiert.

Um das Limit zu erhöhen, muss man in die Modul-Konfiguration unter /etc/apache2/mods-available/fcgid.conf eingreifen und folgenden Eintrag hinzufügen bzw. entsprechend verändern:

<pre name="code" class="php">MaxRequestLen 2097152
</pre>

Damit wird die Beschränkung auf 2 MB erhöht. Sollte für die meisten Zwecke mehr als ausreichen. Anschließend muss der Apache neu gestartet werden, damit die Änderung wirksam wird.

 [1]: http://www.hosteurope.de/