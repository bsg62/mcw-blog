---
title: 'MacBook Pro Retina: Aufwach- und Wi-Fi-Probleme'
author: David Henning
type: post
date: 2012-08-25T15:51:53+00:00
url: /2012/08/macbook-pro-retina-aufwach-und-wi-fi-probleme.html

---
In den vergangenen Tagen hatte ich einige Probleme mit meinem neuen MacBook Pro. Es wachte teilweise nur sehr langsam auf, im schlimmsten Fall dauert es fast 30 Sekunden, bis die Login-Maske kam. Als ob das noch nicht nervig genug wäre, ging nach dem Aufwachen die Wi-Fi-Verbindung nicht bzw. stürzte teilweise das Netzwerk-Panel bei der WLAN-Suche ab. Nach einem Neustart ging zwar alles wieder, aber auch nur, dem die Wi-Fi-Verbindung de- und wieder aktiviert wurde, weil beim normalen Systemstart keine IP-Adresse bezogen werden konnte.

Insbesondere die WLAN-Probleme kamen mir etwas spanisch vor, da ich parallel zum MacBook auch einen neuen Router bekommen habe. Da aber sonst kein Wi-Fi-fähiges Gerät im Haushalt Probleme macht, fiel der neue Router als Fehlerquelle aus.

Nach einiger Recherche in einschlägigen Apple-Foren, kam dann der entscheidende Hinweis für beide Probleme: Bluetooth.

Offenbar blockiert Bluetooth den Aufwachprozess, wenn angemeldete Geräte (hier eine Magic Mouse) nicht gefunden werden. Zusätzlich dazu scheint es eine Funk-Interferenz (WLAN und Bluetooth nutzen beide 2,4 GHz) zu geben, die den Wi-Fi-Verbindungsaufbau stört, was sich dann entweder in og. Absturz äußert oder die IP-Vergabe durch DHCP verhindert.

Sobald ich Bluetooth abschalte, funktioniert alles einwandfrei. Das MacBook wacht sofort auf und die Wi-Fi-Verbindung wird problemlos etabliert.

Natürlich ist das keine endgültige Lösung des Problems, aber man kann sich zumindest solange damit behelfen, bis Apple eine Lösung liefert. Es sieht ohnehin so aus, dass diese Schwierigkeiten nur unter OS X 10.8 auftreten und dürften Updates auf 10.8.2 oder 10.8.3 behoben werden.