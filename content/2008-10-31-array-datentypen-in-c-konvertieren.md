---
title: 'Array-Datentypen in C# konvertieren'
author: David Henning
type: post
date: 2008-10-31T18:42:15+00:00
url: /2008/10/array-datentypen-in-c-konvertieren.html
dsq_thread_id:
  - 497710870

---
Anstatt das Ausgangs-Array mit for() oder foreach() durchzulaufen und dabei das Ziel-Array mit den konvertierten Werten zu füllen, bietet C# dafür eine Lösung über die Methode Array.ConvertAll().

<pre name="code" class="csharp">int[] IntArray = Array.ConvertAll&lt;string, int&gt;(StringArray, delegate(string Value) {
    return Convert.ToInt32(Value);
});
</pre>

Als Beispiel habe ich hier das Konvertieren von Strings nach Integer gewählt, welches über die anonyme Callback-Funktion abläuft. Somit läuft es wesentlich eleganter ab und ist durch Generics flexibel gehalten.