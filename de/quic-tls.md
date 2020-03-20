# Verbindungen verwenden TLS

Unmittelbar nach dem ersten Aufbau einer Verbindung sendet der Initiator einen Krypto-Frame, der mit dem Einrichten des Handshakes der Sicherheitsschicht beginnt. Die Sicherheitsschicht verwendet TLS 1.3.

Es gibt keine Möglichkeit, TLS bei eine QUIC-Verbindung zu deaktivieren oder zu vermeiden. Das Protokoll ist so konzipiert, dass es für Middleboxen schwer zu manipulieren ist, um eine Ossifikation des Protokolls zu verhindern.
