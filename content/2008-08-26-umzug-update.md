---
title: Umzug (Update)
author: David Henning
type: post
date: 2008-08-26T16:01:01+00:00
url: /2008/08/umzug-update.html

---
So, der Umzug ist überstanden. Bei den meisten sollten die DNS-Einträge schon aktualisiert sein.

Dank der neuen Server, läuft nun alles mit MySQL 5. Daher kann ich nun endlich Views (für die zukünftige Multi-Weblog-Funktion) auch außerhalb meiner lokalen Entwicklungsumgebung nutzen, sowie auf MySQLi als objektorientierte Schnittstelle für die Datenbank-Anbindung zurückgreifen.

Letzteres ermöglicht auch ein neues Sicherheitsfeature, das ich momentan in einer alternativen Version zum Testen einsetze: mysqli::prepare(). Damit werden die Werte über einen Platzhalter in die SQL-Abfrage eingefügt und vorher auf Datentyp bzw. SQL-Injections geprüft.

Leider müssen dafür sämtliche Models komplett umgestellt werden, da die Werte nicht mehr direkt in die Abfrage geschrieben werden.