# Wie QUIC funktioniert

In diesem Abschnitt wird beschrieben, wie die grundlegenden Bausteine des QUIC-Transportprotokolls funktionieren, ohne dabei auf alle Bits und Bytes einzugehen. Wenn du deinen eigenen QUIC-Stack implementieren möchtest, sollte dir diese Beschreibung ein allgemeines Verständnis vermitteln. Alle Details findest du in den aktuellen IETF Internet-Entwürfen und RFCs.

1. Eine [Verbindung](quic-connections.md) aufbauen
2. ... die [TLS](quic-tls.md) inkludiert
3. und dann [Streams](quic-streams.md) verwendet