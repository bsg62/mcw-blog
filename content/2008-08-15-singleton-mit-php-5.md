---
title: Singleton mit PHP 5
author: David Henning
type: post
date: 2008-08-15T17:18:02+00:00
url: /2008/08/singleton-mit-php-5.html
dsq_thread_id:
  - 467743946

---
Singleton ist ein sog. Design Pattern, zu Deutsch Entwurfsmuster. Einfach gesagt, sind es Standardlösungen für bestimmte Problemstellungen innerhalb der objektorientierten Programmierung, die immer wieder auftreten.

Eines der einfachsten Muster ist das Singleton. Es stellt sicher, dass von einer Klasse nur eine Instanz erzeugt werden kann und keine weitere. Bei bestimmten Objekten, z.B. für die Datenbank-Verbindung, kann das sehr hilfreich sein. Da ein Singleton über eine statische Methode aufgerufen wird, ist es außerdem möglich dieselbe Instanz einer Klasse ohne Probleme überall im Script aufrufen zu können &#8211; widerrum sehr nützlich bei Datenbanken.

So sieht in Singleton in PHP 5 aus:

<pre name="code" class="php">&lt;?php

class Demo {
	
	/**	 
	 * @access private	 
	 * @static
	 * @var object	 
	 */
	
	private static $_instance = null;

	/**	 
	 * Singleton	 
	 * 
	 * @access public	 
	 * @static	 
	 * @return object self::$Instance	 
	 */
	
	public final static function getInstance() {
		if(!self::$_instance instanceof Demo) {
			self::$_instance = new Demo();
		}
		
		return self::$_instance;
	}

	/**	 
	 * Constructor 	 
	 *
	 * @access private	 
	 */
	
	private function __construct() {
		// Code	
	}

	/**	 
	 * No Clone Wars 	 
	 * 
	 * @final	 
	 * @access private	 
	 */
	
	public final function __clone() {
		return null;
	}

}

?&gt;</pre>

Zuerst wird das statische Attribut _$instance_ als null definiert, gefolgt von der statischen Methode _getInstance()_. Die überprüft, ob in _self::$instance_ bereits eine Instanz der Klasse hinterlegt ist. Falls nein, wird ein neues Objekt erstellt und die Referenz in _self::$instance_ gespeichert. Anschließend gibt _getInstance()_ die Instanz der Klasse zurück.

Wichtig ist, dass der Konstruktor der Klasse als _private_ definiert ist. Somit ist sichergestellt, dass nur _getInstance()_ ihn aufrufen kann und man keine weiteres Objekt der Klasse erzeugen darf. Ebenso muss die Methode ___clone()_ als _private_ deklariert werden, damit das Objekt nicht kopiert werden darf.

Mit folgendem Code erhält man nun die Instanz der Klasse:

<pre name="code" class="php">$demo = Demo::getInstance();</pre>

Dieser Aufruf funktioniert überall, sobald die entsprechende Klasse eingebunden wurde.

Das Singleton Pattern ist aus diversen Gründen recht umstritten. Viele sind der Ansicht, dass man es gar nicht bräuchte. Das mag vielleicht in der normalen Anwendungsentwicklung zutreffen, aber für Web-Programmierung mit PHP, ist es insbesondere bei Datenbank-Verbindungen sinnvoll. Gerade Anfänger begehen oft in dieser Hinsicht, da die alte MySQL-Schnittstelle verwendet und auf die Verwaltung der einzelnen Verbindungen zum Datenbank-Server gepfiffen wird. Eine DB-Klasse mit Singleton stellt sicher, dass es nur eine Verbindung gibt und das entsprechende Objekt überall verfügbar ist.

**Hinweis:** aufgrund der mangelhaften Objekt-Unterstützung in PHP 4, ist ein Singleton dort &#8211; in der oben gezeigten. Form &#8211; nicht möglich.