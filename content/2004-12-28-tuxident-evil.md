---
title: Tuxident Evil
author: David Henning
type: post
date: 2004-12-28T18:21:18+00:00
url: /2004/12/tuxident-evil.html
dsq_thread_id:
  - 467746677

---
Vorab: ich habe nichts gegen Linux und auch nichts gegen Open Source.

Lieber SUSE-Tux,

vorhin habe ich mir das GameStar-Spezial zu Linux gekauft. Auf der DVD ist SUSE Linux 9.1 Personal, diverse Patches, Treiber usw.
  
Die Installation ging schnell und komfortabel. Nach gut 25 Minuten lief alles einwandfrei. Da nur Konqueror mitgeliefert wurde, habe ich mir Firefox runtergeladen und installiert. Verlief nicht minder bequem als unter Windows. Leider weigerte sich der Feuerfuchs beharrlich zu starten. Keine Fehlermeldung. Erst als ich ihn über die Konsole aufgerufen habe, kam die Meldung, daß eine Datei fehlen würde. Interessanterweise lag sie aber im Firefox-Verzeichnis.
  
Nun gut, Konqueror mag ich nicht sonderlich, also lud ich Mozilla runter. Installation problemlos, Mozilla lief. Lustigerweise hat der große Bruder dem Fuchs wohl in den Allerwertesten getreten, sprich Firefox lief nun auch. Schön.
  
Dann war licq an der Reihe. Das war nicht schön. Invisible ging nicht, meine Kontakte wurden nur mit der UIN dargestellt und netterweise sogar teilweise in die entsprechenden UINs umbenannt (was ich erst später wieder mit Miranda gesehen habe). Okay, dann eben gaim.
  
Auf der gaim-Seite gibt&apos;s leider keine rpms für Suse, also her mit dem Quellcode. War eh schon scharf drauf, mal die berühmten Worte »./configure«, »make« und »make install« zu benutzen. Configure meinte, daß das »pkg-packer« und »GLib« fehlen. Alles klar, rpms rausgesucht, installiert und dann das ganze nochmal. Der PKG-Packer ging, GLib wurde als vermisst gemeldet. Da ich das Paket aber installiert hatte und es YaST auch anzeigt, kam mir das ziemlich spanisch vor. Die Idee mittels »su« das ganze als Root auszuführen half auch nichts.
  
Mir wurd&apos;s dann zu doof, also habe ich ein gaim-rpm für SUSE 9.x gesucht. Erfolgreich. Bei der Installation sprangen mir dann die Abhängigkeiten entgegen. Okay, Pakete aufgeschrieben, runtergeladen und beim Installieren gemerkt, daß diese Pakete auch nochmal Abhängigkeiten haben. Juhu.
  
Ende der Geschichte.

Mich stört das ganze jetzt weniger, da ich den festen Willen habe, mich in die Materie Linux einzuarbeiten. Wenn allerdings ein typischer Windows-Nutzer einfach mal SuSE installiert, gefällt es ihm zunächst sicher. Dann will er online gehen, auch kein Problem. Aber spätestens bei gaim, sofern es nicht mitgeliefert wird, wird&apos;s knifflig. Selberkomplilieren kann genauso ausfallen, wie in og. Beispiel und die rpm-Installation ersäuft regelrecht in Abhängigkeiten, trotz Nettigkeiten wie YaST.
  
Da muß einfach noch viel getan werden, bis Linux wirklich massenkompatibel wird. Jeder, der vorher schon mal was mit Windows zu tun hatte, wird bei solchen Problemen nämlich nur eins denken: »Bei Windows klick ich auf setup und gut ist. Bei Linux muß ich zig Kram nachinstallieren, also ist Windows besser.«

Ich lad mir jetzt jedenfalls Knoppix 3.7 runter und installier das dann. SUSE mag mich offenbar nicht :(