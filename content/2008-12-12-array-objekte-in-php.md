---
title: Array-Objekte in PHP
author: David Henning
type: post
date: 2008-12-12T16:40:14+00:00
url: /2008/12/array-objekte-in-php.html
dsq_thread_id:
  - 497710284

---
Bekanntlich sind Arrays in PHP keine Objekte, wie es z.B. in C# oder Java der Fall ist. Dennoch ist es mit den Interfaces und vorgefertigten Klassen der [Standard PHP Library][1] (SPL) möglich, eine Klasse zu entwerfen, die sich wie ein Array verhält. Das mag überflüssig oder überdimensioniert erscheinen, aber ich halte es für ein gutes Beispiel, welche Dinge die SPL möglich macht:

<pre name="code" class="php">&lt;?php

class MyArray implements ArrayAccess, Countable, Iterator {
	
	private $data = array();
	public $length = 0;
	private $position = 0;
	private $keys = array();

	public function __construct() {
		$args = func_get_args();
		
		if(count($args) > 0) {
			foreach ($args as $key => $value) {
				$this->data[$key] = $value;
				$this->length++;
			}
			
			$this->keys = array_keys($this->data);
		}
	}

	public function __destruct() {
		unset($this->data);
	}

	public function __set($offset, $value) {
		return null;
	}

	public function __call($method, $args) {
		return null;
	}

	public function offsetExists($offset) {
		return isset($this->data[$offset]);
	}

	public function offsetGet($offset) {
		return $this->data[$offset];
	}

	public function offsetSet($offset, $value) {
		$this->data[$offset] = $value;
		$this->length++;
		$this->keys = array_keys($this->data);
	}

	public function offsetUnset($offset) {
		unset($this->data[$offset]);
		$this->length--;
		$this->keys = array_keys($this->data);
	}

	public function count() {
		return $this->length;
	}

	public function rewind() {
		$this->position = 0;
	}

	public function next() {
		$this->position++;
	}

	public function key() {
		return $this->keys[$this->position];
	}

	public function current() {
		return $this->data[$this->key()];
	}

	public function valid() {
		if($this->position &lt; $this->length) {
			return true;
		}
		
		return false;
	}
}

?&gt;
</pre>

**Interface ArrayAccess:**

  * offsetExists()
  * offsetGet()
  * offsetSet()
  * offsetUnset()

Diese Methoden sorgen dafür, dass man das Objekt wie ein ganz normales PHP-Array benutzen kann, d.h. eine Einträge hinzufügen, ausgeben oder löschen.

**Interface Countable:**

  * count()

Wie der Name schon sagt, gibt die Methode count() einfach nur die Anzahl der aktuellen Array-Items aus.

**Interface Iterator:**

  * rewind()
  * next()
  * key()
  * current()
  * valid()

Wer vor PHP 4 schon anbord war, wird diese PHP-Funktionen sicher noch kennen, um assoziative Arrays über eine while()-Schleife zu iterieren. Und nichts anderes machen auch die entsprechenden Methoden. Nur sorgen sie in diesem Fall dafür, dass man das Array-Objekt mit foreach() durchlaufen kann.

Zusätzlich sind die magischen Methoden \_\_set() und \_\_call() leer implementiert, so dass man die Eigenschaft $length nicht überschreiben kann und nicht beabsichtigte Methodenaufrufe verhindert werden. Der Konstruktor ermöglicht außerdem wie bei array() beim Initialisieren Werte in das Array zu schreiben.

 [1]: http://www.php.net/~helly/php/ext/spl/