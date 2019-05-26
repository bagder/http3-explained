## Erinnerst du dich an HTTP/2?

Die HTTP/2 Spezifikation [RFC 7540](https://httpwg.org/specs/rfc7540.html) wurde im Mai 2015 veröffentlicht und seitdem weitreichend im Internet und World Wide Web implementiert sowie ausgeliefert.

Anfang 2018 wurden fast 40% der Top 1000 Websites mit HTTP/2 ausgeliefert. Ungefähr 70% aller HTTPS Anfragen, die über Firefox verschickt wurden, bekamen eine HTTP/2 Antwort zurück. Die meistgenutzten Browser, Server und Proxies unterstützen die Spezifikation. 

HTTP/2 behebt eine Fülle an Mängel von HTTP/1, weshalb HTTP-Nutzer nicht mehr zu Übergangslösungen greifen müssen - welche gerade Web Entwickler oft belastet haben.

Eines der Hauptmerkmale von HTTP/2 ist Multiplexing, die Möglichkeit viele logische Streams über die gleiche physische TCP Verbindung zu schicken. Das macht viele Dinge besser und schneller; es macht Überlastungskontrolle viel besser, es lässt User TCP besser nutzen um die Bandbreite besser auszunutzen, die TCP Verbindungen langlebiger - was gut ist, weil Verbindungen öfter die volle Geschwindigkeit aufnehmen können. Header-Komprimierung nutzt dabei weniger Bandbreite.

Mit HTTP/2 nutzen Browser typischerweise *eine* TCP Verbindung zu jedem Host, anstatt der vorherigen *sechs*. Tatsächlich verringert sich die Anzahl der Verbindungen wegen der Verbindungsvereinigung und "Desharding" Techniken von HTTP/2 noch viel wesentlicher.

HTTP/2 löst das Problem des sogenannten HTTP Head-of-line blockings, bei dem Clients so lange warten müssen, bis eine gestellte Anfrage fertig ist, bevor die nächste gestellt werden kann.

![http2 man](../images/h2-man.jpg)
