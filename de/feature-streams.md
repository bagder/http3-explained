## Mehrere Streams innerhalb von Verbindungen

Ähnlich wie SCTP, SSH und HTTP/2 verfügt QUIC über separate logische Streams innerhalb von physischen Verbindungen. Eine Anzahl paralleler Streams, die Daten gleichzeitig über eine einzelne Verbindung übertragen können, ohne die anderen Streams zu beeinträchtigen.

Eine Verbindung ist ein ausgehandelter Aufbau zwischen zwei Endpunkten, der ähnlich wie eine TCP-Verbindung funktioniert. Eine QUIC-Verbindung wird zu einem UDP-Port und einer IP-Adresse hergestellt, aber sobald die Verbindung hergestellt ist, wird sie durch ihre "Verbindungs-ID" verknüpft.

Über eine bestehende Verbindung kann jede Seite Streams erstellen und Daten an das andere Ende senden. Streams werden in richtiger Reihenfolge (in-order) und zuverlässig geliefert - andere Streams können aber in nicht richtiger Reihenfolge (out-of-order) geliefert werden.

QUIC bietet eine Datenflusssteuerung sowohl für Verbindungen als auch für Streams.

Weitere Details findest du in den Bereichen [Verbindungen](quic-connections.md) und
[Streams](quic-streams.md).
