---
title: PHP und FastCGI
author: David Henning
type: post
date: 2007-07-21T22:33:21+00:00
url: /2007/07/php-und-fastcgi.html

---
eine unendliche Geschichte.

Nach dem es etwa schon eine Stunde dauerte, bis PHP 5.2.3 alle benötigten Pakete hatte um unter Ubuntu 7 _./configure_ erfolgreich abzuschließen, ging der Spaß erst richtig los.

Ich will PHP über FastCGI ausführen, da das die deutlich flexiblere Lösung ist. Pro Virtual Host kann man über eine FastCGI-Startdatei die PHP-Binary und die _php.ini_ festlegen. Damit ist es ohne weiteres möglich verschiedene PHP-Versionen auf einem Apache laufen zu lassen.

Soweit, so praktisch. PHP 5 kompiliert fröhlich vor sich hin, was auf einem virtuellen PC natürlich etwas dauert. Währenddessen passe ich schon mal die Konfiguration des Virtual Hosts an und erzeuge einen FCGI-Starter.

Nach etwas Gefrickel in Einstellungen, dem Pfad zu _suexec_ und noch einigen anderen Dingen, wird der Starter nun zwar geladen, aber gleich wieder beendet: _terminated by calling exit with status &apos;0&apos;_.

Nach gut einer Stunde stellte sich dann raus, dass PHP 5.2.3 &#8211; im Gegensatz zu älteren Versionen &#8211; wohl ein Problem damit hat, wenn FastCGI eine normale PHP-Binary aufruft, statt der CGI-Variante. Auf zwei Live-Servern mit PHP 5.1.x geht das noch ohne Probleme.

Wer also vorhat eine neuere Version von PHP 5 mit FastCGI zu betreiben, sollte das von Anfang an beherzigen und sich damit einigen Ärger ersparen.