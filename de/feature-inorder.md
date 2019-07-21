## ‎In-Order Ausliefung

QUIC garantiert die richtige Reihenfolge (in-order) der Zustellung von Streams, jedoch nicht zwischen Streams. Dies bedeutet, dass jeder Stream Daten sendet und die Datenreihenfolge beibehält, aber die Streams das Ziel möglicherweise in einer anderen Reihenfolge erreichen, als wie die Anwendung diese gesendet hat.

Beispiel: Stream A und B werden von einem Server zu einem Client übertragen. Zuerst wird Stream A und dann Stream B gestartet. In QUIC wirkt sich ein verlorenes Paket nur auf jenen Stream aus, zu dem das verlorene Paket gehört. Wenn Stream A ein Paket verliert, Stream B jedoch nicht, setzt Stream B die Übertragung möglicherweise fort und wird abgeschlossen, während das verlorene Paket von Stream A erneut übertragen wird. Dies war unter HTTP/2 nicht möglich.

Hier dargestellt mit einem gelben und einem blauen Stream, die über eine einzige Verbindung zwischen zwei QUIC-Endpunkten gesendet werden. Sie sind unabhängig und können in einer anderen Reihenfolge eintreffen, aber jeder Stream wird zuverlässig und in der richtigen Reihenfolge (in-order) an die Anwendung geliefert.

![zwei QUIC-Streams zwischen zwei Computern](../images/quic-chain-streams.png)
