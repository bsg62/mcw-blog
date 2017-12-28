---
title: BASIC oder wie man sich Stil versaut
author: David Henning
type: post
date: 2004-09-04T21:32:40+00:00
url: /2004/09/basic-oder-wie-man-sich-stil-versaut.html
dsq_thread_id:
  - 467747417

---

  


> It is practically impossible to teach good programming style to students that have had prior exposure to BASIC; as potential programmers they are mentally mutilated beyond hope of regeneration.

Wie wahr, wie wahr&#8230; Basic versaut den Stil, wußte ich schon immer und hier kommt die Bestätigung. Dem Code fehlt einfach eine klare Linie, wie sie z.B. die C-Syntax hat. Außerdem kann ich ihn strukturieren, wie es ich für sinnvoll halte. In Basic ist sowas durch das zeilenbasierte Programmierweise nahezu unmöglich. Ich glaube sogar, daß gerade Anfänger dadurch nur noch mehr unnötig verwirrt werden, gerade weil es keine klare Linie gibt.
  
Ein kurzes Beispiel in Basic, gefolgt von einem in PHP (als Beispiel für die C-Syntax):

<pre><br />
IF i = 10 THEN<br />
 print "blubb"<br />
ENDIF<br />
<br />
if($i == 10) {<br />
 echo "blubb";<br />
}<br />
</pre>

Die PHP-Anweisung könnte ich genauso gut in einer Zeile schreiben, in Basic nicht. Weiterhin halte ich die geschweiften Klammern für deutlich effizienter als die Wörter then und endif. Zwar soll diese Assoziation zur menschlichen Sprache es für Einsteiger erleichtern, aber macht es das für diese wirklich einfacher, wenn ein Wort, statt einer platzsparenden Klammer dort steht? Wohl kaum.
  
Wie man außerdem deutlich sehen kann, ist die echo-Anweisung in PHP klar durch ein Semikolon beendet worden. Basic bietet sowas nicht.
  
Daher hat die C-Syntax bei mir klar die Nase vorn und ich möchte sie keinesfalls mehr missen.