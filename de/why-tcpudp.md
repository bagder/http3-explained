## TCP oder UDP

Wenn wir Head-of-line blocking innerhalb von TCP nicht reparieren können, dann sollten wir theoretisch ein neues Transportprotokoll neben UDP und TCP im Netzwerkstack erstellen können. Oder vielleicht sogar [SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol) nutzen; ein Transportprotokoll mit etlichen der von uns gewünschten Charakteristiken, welches von IETF in [RFC 4960](https://tools.ietf.org/html/rfc4960) standardisiert wurde.

Jedoch ist die Entwicklung von neuen Transportprotokollen in den letzten Jahren nahezu vollständig eingestellt worden, weil diese nur unter schwierigen Umständen im Internet eingesetzt werden können. Der Einsatz neuer Protokolle wird durch viele Firewalls, NATs, Router und andere Netzwerk-Appliances verhindert, welche lediglich TCP oder UDP in der Kommunikation zwischen User und Server zulassen. Ein weiteres Transportprotokoll einzuführen hat die Auswirkung, dass N% der Verbindungen fehlschlagen, weil diese durch Appliances geblockt werden, welche die Verbindungen wegen der Nutzung eines anderen Protokolls als UDP oder TCP als böswillig einstufen. Die N% Fehlerrate wird oft als zu hoch erachtet, um den Aufwand zu rechtfertigen.

Werden Änderungen auf der Ebene des Transportprotokolls im Netzwerkstack vorgenommen, bedeutet das, dass Protokolle über den Kernel des Betriebssystems implementiert werden. Kernel des Betriebssystems zu aktualisieren und auszuliefern ist ein langsamer Prozess, der signifikanten Aufwand mit sich bringt. Viele Verbesserungen von TCP, welche durch IETF standardisiert wurden, sind nicht flächendeckend eingesetzt, weil sie nicht umfassend unterstützt werden. 

## Warum nicht SCTP-over-UDP

SCTP ist ein zuverlässiges Transportprotokoll mit Streams. Für WebRTC gibt es sogar existierende Implementierungen von SCTP über UDP.

Aus folgenden Gründen wurde SCTP-over-UDP als nicht gut genug befunden, um QUIC zu ersetzen:

 - SCTP löst das Head-of-line-blocking Problem für Streams nicht
 - SCTP hat keine solide TLS/Security Geschichte
 - SCTP hat einen 4-way handshake, QUIC bietet 0-RTT
 - QUIC ist ein Bytestream wie TCP, SCTP basiert auf Nachrichten
 - QUIC Verbindungen können zwischen IP Adressen migrieren, was SCTP nicht kann
 
 Für weitere Details zu den Unterschieden empfiehlt sich folgende Übersicht: [A Comparison between SCTP and
QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).