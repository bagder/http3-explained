## User-space

Die Implementierung eines Transportprotokolls im User-space ermöglicht eine schnelle Iteration des Protokolls, da das Protokoll vergleichsweise einfach weiterentwickelt werden kann, ohne dass Clients und Server ihren Betriebssystemkern aktualisieren müssen, um neue Versionen bereitzustellen.

QUIC gibt nichts vor, dass eine zukünftige Implementierung in Betriebssystemkernen verhindern könnte - sollte jemand dies für eine gute Idee halten.

### Viele Implementierungen

Ein offensichtlicher Effekt der Implementierung eines neuen Transportprotokolls im User-space besteht darin, dass wir viele unabhängige Implementierungen erwarten können.

Verschiedene Anwendungen werden wahrscheinlich auf absehbare Zeit unterschiedliche HTTP/3- und QUIC-Implementierungen inkludieren, oder auf solchen aufbauen.