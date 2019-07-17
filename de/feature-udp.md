## Transportprotokoll über UDP

QUIC ist ein Transportprotokoll, das basierend auf UDP implementiert wurde. Wenn Sie Ihren Netzwerkverkehr gelegentlich beobachten, wird QUIC als UDP-Pakete angezeigt.

Basierend auf UDP werden dann auch UDP-Portnummern verwendet, um bestimmte Netzwerkdienste unter einer bestimmten IP-Adresse zu identifizieren.

Alle bekannten QUIC-Implementierungen befinden sich derzeit im User-Space, was eine schnellere Entwicklung ermöglicht, als dies bei Kernel-Space-Implementierungen normalerweise möglich ist.

## Wird es funktionieren?

Es gibt Unternehmen und andere Netzwerkkonfigurationen, die den UDP-Verkehr an anderen Ports als 53 blockieren (für DNS verwendet). Andere drosseln solche Daten auf eine Weise, die die Leistung von QUIC schlechter macht als jene von TCP-basierten Protokollen. Es gibt kein Ende für das, was manche Betreiber tun könnten.

Auf absehbare Zeit muss jeder Einsatz von QUIC-basierten Transporten möglicherweise auf eine andere (TCP-basierte) Alternative zurückgreifen können. Google-Ingenieure haben zuvor gemessene Fehlerraten im niedrigen einstelligen Prozentbereich angegeben.

## Wird es besser?

Wenn sich QUIC als eine wertvolle Bereicherung für das Internet herausstellt, möchten Leute es nutzen und das es in ihren Netzwerken funktioniert - dann können Unternehmen damit beginnen, ihre Hindernisse zu überdenken. Im Laufe der Jahre hat die Entwicklung von QUIC Fortschritte gemacht und die Erfolgsquote beim Aufbau sowie Nutzung von QUIC-Verbindungen über das Internet ist gestiegen.
