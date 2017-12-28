---
title: Ruby ist da
author: David Henning
type: post
date: 2008-01-11T18:00:50+00:00
url: /2008/01/ruby-ist-da.html
dsq_thread_id:
  - 467744057

---
&apos;Ruby&apos; ist der neue Codename für mcw[blog] 2.0. Das Benennungsschema wollte ich ja schon lange ändern, aber mir ist nie etwas vernünftiges eingefallen.

Lustigerweise entstand &apos;Ruby&apos; durch den Nachfolger &apos;Sapphire&apos; (wahrscheinlich Version 3). Inzwischen haben sich so viele Ideen angesammelt, was ich noch besser machen kann, das es nicht mehr sinnvoll ist, es noch in der kommenden Version umzusetzen.

Die Core-App bekommt ein komplett neues Konzept, das an deutlich stärker bzw. ausschließlich objektorientiert sein wird. Soweit es PHP 5.3, evtl. auch schon 6.0 zulassen wird. Die Datenbankschnittstelle z.B. wird nur noch auf MySQLi basieren, um Sicherheits-Features wie mysqli::prepare() nutzen zu können.

Im Gegensatz zu &apos;Ruby&apos; und &apos;miau10&apos; wird das Datenbank-Schema größtenteils unverändert bleiben, da ich mit der aktuellen Struktur sehr zufrieden bin und sie zukunftssicher ist. Dazu wird nur noch MySQL 5 unterstützt, unter anderem wegen der Views im Zusammenspiel mit der Multi-Weblog-Funktion.

Insgesamt betreffen die meisten Ideen &#8211; bisher &#8211; die Core-App, an den eigentlichen Modulen wird sich intern wenig ändern. Nur die Models müssen den neuen Gegebenheiten angepasst werden.

&apos;Sapphire&apos; wird ein wichtiger Schritt in Richtung objektorientierter Vorhölle für prozedurale Web-Programmierer. Trotz der Einschränkungen, dass nur die wenigsten PHP-Kernfunktionen als (brauchbare) Klassen zur Verfügung stehen.