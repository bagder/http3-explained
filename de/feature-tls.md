## TLS 1.3

QUIC verwendete TLS 1.3 ([RFC 8446](https://tools.ietf.org/html/rfc8446)) zur Transportsicherheit und es gibt unter keinen Umständen unverschlüsselte QUIC-Verbindungen.

TLS 1.3 hat einige Vorteile gegenüber älteren TLS-Versionen - ein Hauptgrund für die Verwendung in QUIC ist, dass 1.3 den Handshake so geändert hat, dass weniger Roundtrips erforderlich sind. Dieses Vorgehen reduziert die Protokolllatenz.

In der Google-Version von QUIC wurde eine eigens entwickelte Lösung verwendet.
