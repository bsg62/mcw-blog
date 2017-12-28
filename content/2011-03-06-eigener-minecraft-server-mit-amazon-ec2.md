---
title: Eigener Minecraft-Server mit Amazon EC2
author: David Henning
type: post
date: 2011-03-06T17:45:52+00:00
url: /2011/03/eigener-minecraft-server-mit-amazon-ec2.html
dsq_thread_id:
  - 467748811

---
Nach einigen negativen Erlebnissen mit Spielserver-Anbietern für den <a href="http://www.minestar.de/" target="_blank">MineStar-Server</a>, war klar, dass nur ein eigener Server genug Leistung hat, um wirklich ein gutes Spielerlebnis mit ca. 15+ Leuten zu bieten. Dedizierte Hardware kam aus Preisgründen nicht in Frage, also entschied man sich für einen virtuellen Server in einer Cloud und bisher funktioniert alles tadellos. Angespornt hiervon und den guten Erfahrungen mit den Amazon Web Services, habe ich mich gefragt, ob man nicht einen Server über <a href="http://aws.amazon.com/de/ec2/" target="_blank">Amazons EC2</a> aufsetzen kann und mich daran gemacht.

Mit einer Micro-Instanz von EC2 kostet das ganze pro Stunde 2 Cent, dazu bezahlt man den Traffic. Neukunden bekommen im ersten Jahr einiges kostenlos, Details siehe <a href="http://aws.amazon.com/de/free/" target="_blank">hier</a>. Einen kleinen Server sollte man damit weitgehend kostenlos betreiben können. Da man nur den Verbrauch und keine Grundgebühren bezahlt, kann man notfalls den Server einfach abschalten. 

Die Kosten für Euren Server könnt Ihr im Konto-Bereich von Amazon Web Services mit zweistündiger Verzögerung genau überwachen.

Eine detaillierte Anleitung zum Aufsetzen eines EC2-Servers für Minecraft gibt&#8217;s unter &#8222;weiterlesen &#8230;&#8220;.

<!--more-->Wie funktioniert das ganze nun? Recht simpel, aber es gibt ein paar Anforderungen:

  1. ein Amazon-Account mit gültiger Kreditkarte

  2. eine gültige Telefonnummer, um während der Registrierung für EC2 die Identität zu bestätigen (man wird angerufen und muss eine von der Website dargestellte PIN eingeben, es entstehen keine Kosten)

  3. grundlegende Kenntnisse der Unix-Shell (nicht zwingend, aber auf jeden Fall ratsam für die Verwaltung des Minecraft-Servers)

Englisch und ein paar grundsätzliche Kenntnisse zum Thema Server setze ich einfach voraus. ;)

**Registrierung und Login:**

<p style="padding-left: 30px;">
  <a href="http://aws.amazon.com/de/ec2/" target="_blank">Registriert Euch hier für Amazon EC2 (ganz unten)</a> und wartet auf die Bestätigungen per Mail.
</p>

<p style="padding-left: 30px;">
  Loggt Euch in die <a href="https://console.aws.amazon.com/" target="_blank">Amazon Web Services Management Console</a> ein und klickt auf den Reiter EC2.
</p>

**Erstellen des EC2-Servers:**

<p style="padding-left: 30px;">
  Klickt auf &#8222;Launch Instance&#8220; und wählt &#8222;Basic 32-bit Amazon Linux AMI 2010.11.1 Beta&#8220;.
</p>

<p style="padding-left: 30px;">
  Wählt unter  &#8222;Instance Type&#8220; Micro aus und fahrt fort.
</p>

<p style="padding-left: 30px;">
  Die &#8222;Advanced Instance Options&#8220; lasst Ihr so wie sie sind und fahrt fort.
</p>

<p style="padding-left: 30px;">
  Dem Key &#8222;Name&#8220; könnt Ihr im entsprechenden Feld für &#8222;Value&#8220; den Namen Eures Servers geben, also z.B. &#8222;Minecraft&#8220; und fahrt fort.
</p>

<p style="padding-left: 30px;">
  Lasst ein neues Key Pair mit dem Namen Eurer Wahl erstellen und speichert die Datei ab.
</p>

<p style="padding-left: 30px;">
  Erstellt eine neue Security Group mit einem Namen Eurer Wahl und fahrt fort.
</p>

<p style="padding-left: 30px;">
  Anschließend seht Ihr eine Übersicht Eurer Einstellungen und könnt die Server-Instanz starten.
</p>

**Firewall-Konfiguration des Servers**

<p style="padding-left: 30px;">
  Klickt in der EC2 Management Console links auf Security Groups und wählt Eure vorhin erstellte Gruppe an.
</p>

<p style="padding-left: 30px;">
  Erstellt eine neue Regel mit folgenden Einstellungen:
</p>

<ul style="padding-left: 30px;">
  <li>
    Connection Method: Custom
  </li>
  <li>
    Protocol: TCP
  </li>
  <li>
    From Port/To Port: 25565
  </li>
  <li>
    Scource: 0.0.0.0/0
  </li>
</ul>

<p style="padding-left: 30px;">
  Damit hat man nun über den Standard-Port von Minecraft Zugriff auf Euren Server.
</p>

**Einloggen auf dem Server**

<p style="padding-left: 30px;">
  Als Windows-User benötigt Ihr für den Login PuTTY als SSH-Client.
</p>

<p style="padding-left: 30px;">
  PuTTY gibt&#8217;s <a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html" target="_blank">hier</a> und besorgt Euch auch noch gleich PuTTYgen.
</p>

<p style="padding-left: 30px;">
  Da PuTTY keine Key-Pair-Dateien im PEM-Format mag, muss die Datei konvertiert werden: startet PuTTYgen, wählt &#8222;File&#8220; -> &#8222;Load private key&#8220;, wählt die Key-Pair-Datei an, das Ihr vorhin erstellt habt und klickt auf &#8222;Save private key&#8220;.
</p>

<p style="padding-left: 30px;">
  Öffnet nun PuTTY, tragt als Hostname &#8222;ec2-user@Public-DNS-des-Servers&#8220; (den Public DNS findet Ihr in der Beschreibung des Servers) ein, z.B.: ec2-user@ec2-43-51-130-107.eu-west-1.compute.amazonaws.com
</p>

<p style="padding-left: 30px;">
  Klickt in der linken Navigation von PuTTY auf Connection -> SSH -> Auth und gebt unter &#8222;Private key file for authentication&#8220; Eure konvertierte Key-Pair-Datei an.
</p>

<p style="padding-left: 30px;">
  Geht zurück zu &#8222;Session&#8220; und klickt unten auf &#8222;Open&#8220;.
</p>

<p style="padding-left: 30px;">
  Willkommen in der Shell Eures Servers. Lasst das Fenster offen. Wir brauchen es später noch.
</p>

**Server-Dateien hochladen**

<p style="padding-left: 30px;">
  Man könnte die Dateien auf die harte Tour via Shell hochladen, aber das will ich hier niemanden antun. Stattdessen empfehle ich <a href="http://winscp.net/" target="_blank">WinSCP</a> oder unter OS X <a href="http://cyberduck.ch/" target="_blank">Cyberduck</a>.
</p>

<p style="padding-left: 30px;">
  Installiert WinSCP und startet es.
</p>

<p style="padding-left: 30px;">
  Klickt auf &#8222;Neu&#8220; und gebt folgende Daten an:
</p>

<ul style="padding-left: 30px;">
  <li>
    Rechnername: Public DNS des Servers
  </li>
  <li>
    Benutzername: ec2-user
  </li>
  <li>
    Passwort: bleibt leer
  </li>
  <li>
    Datei mit privatem Schlüssel: Eure Key-Pair-Datei
  </li>
</ul>

<p style="padding-left: 30px;">
  Klickt auf anmelden und Ihr landet im Nutzerverzeichnis Eures Servers. Ihr könnt nun von hier aus wie mit einem normalen FTP-Programm die Server-Dateien des Minecraft-Servers hochladen.
</p>

**Starten und Verwalten des Servers**

<p style="padding-left: 30px;">
  Über die noch offene PuTTY-Session könnt Ihr nun Euren Server starten. Eine genaue Erklärung spare ich mir an dieser Stelle, da dies schon von Anderen zigfach und detalliert beschrieben wurde, u.A. im <a href="http://www.minecraftwiki.net/wiki/Setting_up_a_server#Linux" target="_blank">Minecraft-Wiki</a> oder <a href="http://www.minecraftforum.net/viewtopic.php?f=1013&t=23122" target="_blank">Minecraft-Forum</a>. Dort findet Ihr auch Informationen über die Verwaltung des Servers.
</p>

So, damit solltet Ihr halbwegs gerüstet sein, um einen kleinen Minecraft-Server mit EC2 aufzusetzen. Fragen und Anmerkungen bitte in die Kommentare.