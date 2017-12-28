---
title: Ein paar Änderungen
author: David Henning
type: post
date: 2011-03-05T19:27:07+00:00
url: /2011/03/ein-paar-anderungen.html
dsq_thread_id:
  - 480657197

---
Nach langer Abstinenz durch Blog-Unlust, wird es Zeit wieder etwas zu schreiben. Ich habe in vergangenen Tagen einige technische Änderungen vorgenommen:

  * Ein Großteil der statischen Inhalte (Bilder, CSS-Dateien, JavaScripts etc.) wird nun über ein Content Delivery Network (CDN) bereitgestellt. Hierzu verwende ich ich die Services <a href="http://aws.amazon.com/de/s3/" target="_blank">Amazon S3</a> bzw. <a href="http://aws.amazon.com/de/cloudfront/" target="_blank">Amazon CloudFront</a>. S3 übernimmt die eigentliche Speicherung der Dateien innerhalb des Amazon-Netzwerks. CloudFront bezieht die Daten von S3 und stellt sie wahlweise als Download- oder Streaming-Inhalt über das weltweite CloudFront-Netzwerk bereit. Realisiert wird das ganze über das WordPress-Plug-In <a href="http://wordpress.org/extend/plugins/w3-total-cache/" target="_blank">W3 Total Cache</a>, das die Dateien zu S3 überträgt und sich um die URL-Umschreibung zu CloudFront kümmert.
    
    Das klingt nun extrem überdimensioniert und ist es eigentlich auch. Mir geht es dabei um den technischen Aspekt, wie man sowas realisiert und die sich daraus ergebenden Vorteile von Cloud Hosting Services. Abgesehen davon, ist es unschlagbar günstig. Man zahlt keinerlei Grundgebühren, es wird nur abgerechnet, was man wirklich verbraucht. Für meine Verhältnisse in Sachen Traffic und Zugriffe, kostet das nur ein paar Cent im Monat.

  * Nach dem ich zwischenzeitlich wieder Google Analytics als Statistikdienst genutzt hatte, bin ich nun auf <a href="http://piwik.org/" target="_blank">Piwik</a> umgestiegen. Piwik ist eine Open Source-Lösung, die fast alles kann, was Analytics auch bietet, läuft aber lokal auf meinem Web-Server. IP-Adressen werden ausschließlich anonymisiert verwendet.
    
    Wer nicht von Piwik erfasst werden möchte, kann sich <a href="http://analytics.madcatswelt.org/index.php?module=CoreAdminHome&action=optOut" target="_blank">hier</a> per Cookie ausschließen lassen.

  * Wie oben schon erwähnt, setze ich nun W3 Total Cache ein. Neben der Bereitstellung der statischen Inhalte über ein CDN, bietet es vor allem diverse Caching-Systeme für Dateien, Datenbank-Inhalte, Objekte oder auch HTTP-Kompression. Die Ladezeiten sollten so angenehmer sein und gleichzeitig wird der Server geschont.

So, das war&#8217;s dann erstmal. In Zukunft werden wieder mehr Einträge folgen, wie üblich hauptsächlich über Technik, Web-Entwicklung oder Spiele.