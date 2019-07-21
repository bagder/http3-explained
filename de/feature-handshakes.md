# Schnelle Handshakes

QUIC bietet einen Verbindungsaufbau sowohl mit 0-RTT als auch 1-RTT. Das bedeutet, dass QUIC beim Aufbau einer neuen Verbindung bestenfalls keine zusätzlichen Roundtrips benötigt. Der Schnellere von beiden, der 0-RTT-Handshake, funktioniert nur, wenn zuvor eine Verbindung zu einem Host hergestellt und ein Geheimnis dieser Verbindung zwischengespeichert wurde.

## Früher Daten versenden

Mit QUIC kann ein Client Daten bereits zu 0-RTT-Handshakes hinzufügen. Diese Funktion ermöglicht es einem Client, Daten so schnell wie möglich an den Peer zu übermitteln. Auf diese Weise kann der Server natürlich noch früher antworten und Daten zurücksenden.
