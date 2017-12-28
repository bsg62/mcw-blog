---
title: Denial of Service …
author: David Henning
type: post
date: 2005-01-29T01:16:54+00:00
url: /2005/01/denial-of-service.html
dsq_thread_id:
  - 467746485

---
Wie bringt man Norton Internet Security (NIS) dazu, einen Rechner, den es eigentlich beschützen sollte, einer Self-DoS-Attacke zu unterziehen? Klingt sehr merkwürdig oder? Geht aber, wie der Chaos Computer Club sehr erfolgreich gezeigt hat:

Alles, was man wissen muß, sind die IPs der Nameserver, die das Opfer gerade benutzt. Mit einem kleinen Tool schickt man dann an das Opfer IP-Pakete mit gefälschter Absenderadresse, nämlich den DNS-IPs, auf den Port 666. NIS hält das ganze für einen Trojaner-Angriff und sperrt damit sofort den Zugriff auf die Absender-IP-Adressen der gefälschten Pakete. Domain-Namen können dann nicht mehr in ihre IP-Adressen aufgelöst werden, sprich surfen ist nahezu unmöglich, genauso wie andere Online-Aktivitäten, die eine DNS-Auflösung erfordern.

Das und noch viel mehr, demonstriert der CCC Ulm in seinem Vortrag über Personal-Firewalls. Wer gut zwei Stunden Zeit mitbringt, kann sich das ganze unter folgender URL runterladen: <http://ulm.ccc.de/chaos-seminar/personal-firewalls/recording.html>