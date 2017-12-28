---
title: SOAP mit PHP
author: David Henning
type: post
date: 2010-05-23T14:48:27+00:00
url: /2010/05/soap-mit-php.html
dsq_thread_id:
  - 530380501

---
Die SOAP-Schnittstelle von PHP ist eine tolle Sache. Ihr Aufbau ist durchdacht und einfach zu verstehen. Als Entwickler kann man mit sehr wenigen Zeilen wirklich viel erreichen und es wird einem die gesamte XML-Ebene eines Zugriffs erspart. Leider gibt es aber ein großes Manko: die mangelhafte Dokumenation für die Datenübergabe. Die Beispiele auf php.net enthalten nur ganz einfache Strukturen, und keine Complex Types mit Attributen, gleichen Elementnamen auf derselben Ebene etc.

Im Zuge eines großen Shop-Projekts musste ich mich tiefer in die Schnittstelle einarbeiten und immer wieder stundenlang in den entsprechenden Kommentaren auf php.net oder via Suchmaschine recherchieren bzw. hirnlos rumprobieren, weil bei der Suche nichts sinnvolles rauskam. Daher nun an dieser Stelle ein paar einfache Beispiele, bestehend aus der XML-Struktur (den SOAP-Envelope spare ich mir) und dem entsprechenden Array-Aufbau.

**Attribute**

Gewünschtes XML:

<pre name="code" class="html">&lt;basket&gt;
    &lt;item id="1" value="499"&gt;Apple iPad WiFi 16 GB&lt;/item&gt;
&lt;/basket&gt;
</pre>

PHP-Array:

<pre name="code" class="php">Array
(
    [basket] =&gt; Array
        (
            [item] =&gt; Array
                (
                    [_] =&gt; &gt;Apple iPad WiFi 16 GB
                    [id] =&gt; 1
                    [value] =&gt; 499
                )

        )

)
</pre>

**Elemente mit gleichen Namen in der derselben Ebene**

An obigem Beispiel erkennt man, dass die Elementnamen über die Array-Schlüssel festgelegt werden. Möchte man nun mehrere Elemente mit dem gleichen Namen in derselben Ebene haben, wird daraus nichts, weil sie sich gegenseitig überschreiben würden. Daher werden kommt um die Elemente noch ein weiteres, nun aber numerisches Array.

Gewünschtes XML:

<pre name="code" class="html">&lt;basket&gt;
    &lt;item id="1" value="499"&gt;Apple iPad WiFi 16 GB&lt;/item&gt;
    &lt;item id="2" value="999"&gt;Apple MacBook&lt;/item&gt;
&lt;/basket&gt;
</pre>

PHP-Array:

<pre name="code" class="php">Array
(
    [basket] =&gt; Array
        (
            [0] =&gt; Array
                (
                    [item] =&gt; Array
                        (
                            [_] =&gt; Apple iPad WiFi 16 GB
                            [id] =&gt; 1
                            [value] =&gt; 499
                        )

                )

            [1] =&gt; Array
                (
                    [item] =&gt; Array
                        (
                            [_] =&gt; Apple MacBook
                            [id] =&gt; 2
                            [value] =&gt; 999
                        )

                )

        )

)
</pre>

**Element mit Attributen und Kinder-Elementen**

Gewünschtes XML:

<pre name="code" class="html">&lt;basket date="2010-05-23"&gt;
    &lt;items&gt;
        &lt;item id="1" value="499"&gt;Apple iPad WiFi 16 GB&lt;/item&gt;
        &lt;item id="2" value="999"&gt;Apple MacBook&lt;/item&gt;
    &lt;/items&gt;
&lt;/basket&gt;
</pre>

PHP-Array:

<pre name="code" class="php">Array
(
    [basket] =&gt; Array
        (
            [date] =&gt; 2010-05-23
            [items] =&gt; Array
                (
                    [0] =&gt; Array
                        (
                            [item] =&gt; Array
                                (
                                    [_] =&gt; Apple iPad WiFi 16 GB
                                    [id] =&gt; 1
                                    [value] =&gt; 499
                                )

                        )

                    [1] =&gt; Array
                        (
                            [item] =&gt; Array
                                (
                                    [_] =&gt; Apple MacBook
                                    [id] =&gt; 2
                                    [value] =&gt; 999
                                )

                        )

                )

        )

)
</pre>

Ich hoffe, dass ich mit diesen einfachen Beispielen einigen Entwicklern die lästige Sucherei bzw. das Rumprobieren ersparen konnte.