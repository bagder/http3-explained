# Daten im Voraus

QUIC bietet 0-RTT und 1-RTT Handshakes, welche die Zeit des Verhandelns sowie den Aufbau einer neuen Verbindung verkürzen. Vergleiche diesen Prozess mit dem 3-Schritt Handshake von TCP.

Zusätzlich bietet QUIC "Daten im Voraus" Support, welcher größeren Datenfluss erlaubt und im Vergleich zu TCP Fast Open benutzerfreundlicher ist.

Mit dem Stream-Konzept kann sofort eine weitere logische Verbindung zum gleichen Host aufgebaut werden, ohne auf das Ende einer bereits bestehenden Verbindung warten zu müssen.

## TCP Fast Open ist problematisch

TCP Fast Open wurde als [RFC 7413](https://tools.ietf.org/html/rfc7413) im Dezember 2014 veröffentlicht. Diese Spezifikation beschreibt, wie Applikationen Daten zum Server bereits im ersten TCP SYN Paket übermitteln können.

Der tatsächliche Support für dieses Feature hat lange gedauert und ist bis ins heutige Jahr 2018 mit Problemen gespickt. Diejenigen, die den TCP-Stack implementiert haben, hatten Probleme und somit auch Applikationen, die die Vorteile dieses Features nutzen wollten. Dies gilt sowohl für das Verständnis der zu aktivierenden Betriebssystemversionen als auch für das Lösen von Problemen im Zusammenhang mit der mangelnden Clientseitigen Unterstützung (backdown). Viele Netzwerke konnten identifiziert werden, die TFO-Traffic stören und daher den reibungslosen Ablauf von TCP-Handshakes beeinträchtigen.