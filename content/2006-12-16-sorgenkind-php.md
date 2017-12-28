---
title: Sorgenkind PHP
author: David Henning
type: post
date: 2006-12-16T15:47:22+00:00
url: /2006/12/sorgenkind-php.html

---
Es scheint, daß innerhalb des PHP-Teams niemand sonderlich daran interessiert ist für mehr Sicherheit zu sorgen. [Stefan Esser][1], der Gründer des PHP Security Response Teams, ist inzwischen zurückgetreten, weil ihm nur Steine in den Weg gelegt wurden.

Die Sicherheitsproblematik in PHP will dort wohl niemand einsehen. Ich frage mich nur, warum das so ist? Gerade eine so stark verbreitete Sprache muß mehr in dieser Hinsicht tun und nicht alles dem Programmierer überlassen. Besonders in diesem Fall, da PHP wegen seiner Einfachheit sehr gerne von Anfängern benutzt wird, die sich mit den Sicherheitsaspekten im Netz überhaupt nicht auseinandersetzen.

Am besten wäre es wohl, wenn man PHP 7 (Version 6 dürfte schon zu weit fortgeschritten sein) komplett neu aufbaut und schreibt. Aktuell hat PHP noch genug andere Defizite, die endlich behoben werden sollten.

Ein paar Vorschläge für PHP 7:

  * einheitliche Namensgebung für alle integrierten Funktionen bzw. Methoden
  * eigene Funktionen- bzw. Methodenbezeichner müssen case-sensitive sein
  * optionale Variablen-Deklaration, deren Datentyp von PHP nicht mehr geändert wird 
  * optionale Datentypangabe bei Funktions- bzw. Methodenparametern 
  * statt Superglobals eine objektorientierte Schnittstelle für HTTP- und Servervariablen, die man entweder über Interfaces selbst implementieren oder mit vorgefertigten Methoden benutzen kann.
  * bessere Kontrollmöglichkeiten von Benutzereingaben, dazu zählen: Datentyp, Länge, reguläre Ausdrücke und vorgegebene Werte zum Vergleich etc.
  * die Möglichkeit Objekte im Speicher zu halten oder speichern zu können (als Ersatz für das Session-Handling)

Die »Konkurrenz« hat diese Möglichkeiten, insbesondere [Ruby on Rails][2]. Letzteres ist natürlich viel mehr ein Framework, aber das ist kein Argument, warum man diese Dinge nicht auch in PHP implementieren sollte.

 [1]: http://blog.php-security.org/archives/61-Retired-from-securityphp.net.html
 [2]: http://rubyonrails.org/