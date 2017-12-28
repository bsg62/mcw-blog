---
title: Quo vadis, Firefox?
author: David Henning
type: post
date: 2012-01-14T19:10:33+00:00
url: /2012/01/quo-vadis-firefox.html
dsq_thread_id:
  - 539199652

---
Angeregt von einem <a href="http://www.chip.de/artikel/Firefox-10-11-und-12-Feature-Vorschau-fuer-den-Mozilla-Browser_53358770.html" target="_blank">Artikel</a> meines künftigen Arbeitgebers über die Weiterentwicklung von Firefox in den Versionen 10, 11 und 12, möchte ich ein paar Gedanken über die merkwürdige Prioritätenvergabe der Mozilla Foundation loswerden.

Die Features der drei kommenden Versionen konzentrieren sich fast ausschließlich auf Komfort und die weitere Vereinheitlichung der Benutzeroberfläche. Natürlich sind dies bei einem Browser sehr wichtige Faktoren, aber meiner Meinung nach, hat Firefox viel größere Defizite, die Angriff genommen werden sollten.

### Projekt Electrolysis

Wie der Name schon sagt, geht es um die Trennung des Ganzen in seine Bestandteile. Auf Firefox bezogen, soll das Projekt Electrolysis auf eine Aufspaltung des großen Firefox-Prozesses in mehrere Prozesse ermöglichen. Google setzt eine solche Architektur von Anfang an in Chrome ein. Es gibt einen Hauptprozess und für jeden geöffneten Tab einen weiteren Prozess. Desweiteren wird jedes Plug-In sowie jede Extension in je einen weiteren Prozess ausgelagert. Damit erreicht Google einen stabilen, effizienten Browser, der den Arbeitsspeicher nicht unnötig belastet und selbst bei einem Absturz eines Tabs, Plug-Ins etc.  immer noch weiterlaufen kann. Apple und Microsoft fanden diese Idee so gut, dass Safari 5 und der Internet Explorer 9 ein ähnliches Prozess-Modell verwenden.

Mozilla wollte ebenfalls auf den Zug aufspringen und hat daher das Projekt Electrolysis ins Leben gerufen. Als ersten Schritt wurde die Ausgliederung von Plug-In-Prozessen in Angriff genommen, die mit Firefox 3.6.4 vor knapp 18 Monaten ihren Weg in die offiziellen Releases fand.

Schritt 2 war die Teilung in den Hauptprozess und Einzelprozesse für die offenen Tabs. Da Mozilla offensichtlich keine Veranlassung sah, dass dieses Feature möglichst schnell in die Desktop-Version Einzug hält, wurde es zuerst in Fennec, die mobile Version von Firefox, implementiert &#8212;  durchaus sinnvoll, um mit den begrenzten Ressourcen effizient umzugehen. Seit März vergangenen Jahres ist Fennec im Android Market erhältlich. Viel getan hat sich seit dem nichts mehr. Die Projekt-Seite im Mozilla Wiki wurde zuletzt im April 2011 aktualisiert und auch an anderer Stelle finden sich kaum Hinweise, wie es mit der Entwicklung von Electrolysis weitergeht.

In Anbetracht des hohen Speicherbedarfs von Firefox, insbesondere wenn Extensions im Spiel sind, finde ich es sehr schade, dass sich hier nicht mehr tut oder der Fortschritt nur sehr mangelhaft kommuniziert wird. Firefox würde enorm von der Prozess-Aufteilung profitieren, sei es in Sachen RAM-Verbrauch, als auch Stabilität und Geschwindigkeit.

### JavaScript

Sicherlich kann man der Mozilla Foundation zu Gute halten, dass sich die JavaScript-Leistung seit dem Release von Firefox 4 und 9 signifikant verbessert hat, dennoch besteht nach wie vor großer Aufholbedarf gegenüber Chrome. Mit <a href="https://wiki.mozilla.org/Platform/Features/IonMonkey" target="_blank">IonMonkey </a>ist ein neuer <a href="http://de.wikipedia.org/wiki/Just-in-time-Kompilierung" target="_blank">JIT </a>in Arbeit, der das bestehende Konstrukt aus JägerMonkey bzw. TraceMonkey ablösen soll. Wie die Entwickler zugegeben haben, ist die aktuelle Architektur nur sehr schwer zu optimieren und daher wird IonMonkey zum Großteil komplett neu geschrieben.

Diese Bestrebung ist sehr löblich und wird sicher auch Früchte tragen, aber sie kommt reichlich spät und wird zu dem auch viel Zeit in Anspruch nehmen. Wir können froh sein, wenn IonMonkey am Jahresende seinen Weg in die offiziellen Releases findet. Aber die Konkurrenz schläft nicht und Google hat schon ein paar mal bewiesen, dass sich massiv an der Performance-Schraube ihres eigenen JITs, V8, drehen können. Verbesserungen von 10 &#8211; 30% mit einem Release waren keine Seltenheit. Microsoft, Opera und Apple werden ebenfalls daran arbeiten die JavaScript-Leistung ihrer Browser deutlich zu verbessern.

Firefox läuft hier Gefahr ins Hintertreffen zu geraten und daher sollten die Bestrebungen für IonMonkey unbedingt verstärkt werden. JavaScript ist heute unverzichtbarer Bestandteil der meisten Websites und Rich Internet Applications werden zunehmend wichtiger, insbesondere da Microsoft endlich eingesehen hat, dass der Internet Explorer technisch weiterkommen muss.

### Profile

Wenn Firefox sich seltsam verhält, oft abstürzt oder sich anderweitig unangenehm bemerkbar macht, wundern sich viele, dass eine Neuinstallation nichts bringt. Die Universalwaffe gegen Windows-Probleme versagt hier kläglich, weil die Nutzerdaten, Einstellungen und Extensions als separates Profil in den Anwendungsdaten bzw. im Home-Verzeichnis gespeichert werden und dort auch bleiben, wenn man den Browser deinstalliert. Wird Firefox neu installiert, greift er auf dasselbe Profil wie die vorherige Installation zu und hat daher auch die gleichen Probleme.

Probleme mit den Profilen ziehen sich leider immer wieder quer durch die gesamte Geschichte von Firefox und gab es auch schon vorher in der Mozilla Suite &#8212; heute besser bekannt als SeaMonkey. Warum das so ist, ist bisher nicht klar geworden. Im Verlauf der Firefox-Entwicklung hat Mozilla in den Profilen einiges verändert.

Vieles, was früher in simplen Text-Dateien gespeichert wurde, befindet sich heute in SQLite-Datenbanken. Damit konnte man z.B. Dinge wie die AwesomeBar, die intelligente Adressleiste, realisieren. Leider ergaben sich hierbei aber neue Probleme. Insbesondere die Browsing History wird sehr ausgedehnt gespeichert, damit aber sehr groß und mit der Zeit auch immer langsamer. Wer keine SSD sein Eigen nennt, kennt die teils langen Startzeiten von Firefox, die unmittelbar damit zusammenhängen. Selbst wenn das Fenster inzwischen geöffnet wurde und man etwas in die Adresszeile eingibt, kann es teilweise mehrere Sekunden dauern, bis überhaupt eine Reaktion erfolgt.

Selbst neue, frische Profile sind manchmal kein Garant dafür, dass Firefox rund läuft. Erst letztens gab es in meinem Freundeskreis den Fall, dass der Browser mit einem ein paar Wochen alten Profil plötzlich regelmäßige Aussetzer hatte und nicht mehr reagierte. Erst ein ganz neues Profil beseitigte dieses Problem.

All dies ist nur ein kleiner Teil mir bekannter Profilprobleme. Mozilla sollte daher schleunigst etwas dagegen unternehmen.

### Fazit

Wie man unzweifelhaft sieht, hat Firefox viele technische Macken bishin zu wirklich großen Handicaps. Vielen Nutzern mag dies aktuell noch egal sein, weil sie nicht betroffen sind oder es ihnen egal ist, wie schnell ihr Browser ist. Derzeit ist auch der Erfolg von Chrome kein Anzeichen dafür, dass Firefox auf einem absteigenden Ast wäre. Der steigende Anteil von Chrome geht zum Großteil zu Lasten des Internet Explorers. Trotzdem sehe ich die Mozilla Foundation in der Pflicht endlich angemessen auf og. Problematiken zu reagieren.

Wie bereits erwähnt, schläft die Konkurrenz nicht. Google hat mit Chrome eindrucksvoll gezeigt, wie man einen modernen, schlanken Browser entwickelt. Mozilla tut sich offenbar schwer, Firefox und Gecko entsprechend umzustellen, was für mich als Programmierer bedeutet, dass dort noch viele Altlasten mitgeschleppt werden (müssen). Daher wäre es wohl an der Zeit, einen Strich zu ziehen und vieles komplett neu anzugehen, wie es z.B. schon bei IonMonkey getan wird. Mit einem modernen Aufbau der Interna wäre Firefox zukunftssicher und Mozilla würde sich in der Weiterentwicklung sehr viel leichter tun.