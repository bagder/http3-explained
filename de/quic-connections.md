# Verbindungen

Eine QUIC-Verbindung ist eine einzelne Konversation zwischen zwei QUIC-Endpunkten. Der Verbindungsaufbau von QUIC kombiniert die Versionsaushandlung mit den kryptografischen und Transport-Handshakes, um die Latenz beim Verbindungsaufbau zu verringern.

Um tatsächlich Daten über eine solche Verbindung zu senden, müssen ein oder mehrere Streams erstellt und verwendet werden.

## Verbindungs-ID

Jede Verbindung verfügt über eine Reihe von Verbindungskennungen oder Verbindungs-IDs, von denen jede zur Identifizierung der Verbindung verwendet werden kann. Verbindungs-IDs werden unabhängig von den Endpunkten ausgewählt; jeder Endpunkt wählt die Verbindungs-IDs aus, die sein Peer verwendet.

Die Hauptfunktion dieser Verbindungs-IDs besteht darin, sicherzustellen, dass Änderungen in der Adressierung auf niedrigeren Protokollschichten (UDP, IP und darunter) nicht dazu führen, dass Pakete einer QUIC-Verbindung an den falschen Endpunkt gesendet werden.

Durch die Nutzung der Verbindungs-ID können Verbindungen auf eine Weise zwischen IP-Adressen und Netzwerkschnittstellen migrieren, wie dies TCP niemals könnte. Durch die Migration kann beispielsweise ein laufender Download von einer Mobilfunkverbindung zu einer schnelleren WLAN-Verbindung geändert werden, wenn der Benutzer sein Gerät an einen Standort mit WLAN-Verbindung bringt. Ebenso kann der Download über die Mobilfunkverbindung erfolgen, wenn das WLAN nicht mehr verfügbar ist.

## Portnummern

QUIC ist auf UDP aufgebaut, daher wird ein 16-Bit-Portnummernfeld verwendet, um eingehende Verbindungen zu unterscheiden.

## Versionsaushandlung

Eine von einem Client stammende QUIC-Verbindungsanforderung teilt dem Server mit, welche QUIC-Protokollversion er sprechen möchte. Der Server antwortet mit einer Liste der unterstützten Versionen, aus denen der Client auswählen kann.
