## TCP Head-of-line blocking

HTTP/2 nutzt TCP, wenngleich es im Gegensatz zu früheren HTTP Versionen weniger TCP Verbindungen benötigt. TCP ist ein Protokoll für eine zuverlässige Übertragung und kann als imaginäre Kette zwischen zwei Computern gesehen werden. Was vom ersten Computer über das Netzwerk übermittelt wird, wird schließlich beim zweiten Computer in der gleichen Reihenfolge ankommen (oder die Verbindung ist unterbrochen).

![Eine TCP Kette zwischen zwei Computern](../images/tcp-chain.png)

Mit HTTP/2 machen Browser zehn oder hunderte Übertragungen gleichzeitig über eine einzige TCP Verbindung.

Wenn ein einziges Paket fallen gelassen wird oder im Netzwerk irgendwo zwischen den beiden Endpunkten - welche über HTTP/2 kommunizieren - verloren geht, dann wird die gesamte TCP Verbindung solange gestoppt, bis das verlorene Paket wieder übertragen wurde und ihren Weg zum Ziel gefunden hat. Weil TCP diese "Kette" darstellt, muss alles - sollte eine Verbindung plötzlich fehlen - was nach der verlorenen Verbindung kommen würde, warten.

Eine Illustration der Ketten-Metapher, wenn zwei Streams über diese Verbindung versendet werden. Ein roter und ein grüner Stream:

![Die Kette zeigt zwei Verbindungen in unterschiedlichen Farben](../images/tcp-chain-streams.png)

Es resultiert ein TCP basierender Head-of-line block!

Steigt die Verlustrate von Paketen, liefert HTTP/2 eine immer schlechtere Performance. Bei einer 2%-igen Verlustrate (was wohlgemerkt eine schlechte Netzwerkqualität ist) haben Tests gezeigt, dass HTTP/1 User normalerweise besser aussteigen - weil diese bis zu sechs TCP-Verbindungen haben, auf welche verlorene Pakete aufgeteilt werden können. Das bedeutet, dass für jedes verlorene Paket eine andere Verbindung weiterarbeiten kann.

Dieses Problem zu beheben ist nicht einfach - wenn überhaupt mit TCP möglich.

## Unabhängige Streams vermeiden den Block

Mit QUIC gibt es noch immer einen Verbindungsaufbau zwischen den beiden Endpunkten, welcher die Verbindung sicher und den Datentransport zuverlässig macht.

![Eine QUIC Kette zwischen zwei Computern](../images/tcp-chain.png)

Wenn zwei unterschiedliche Streams über diese Verbindung aufgebaut werden, werden diese unabhängig voneinander behandelt, sodass - sollte eine Verbindung für einen der Streams verloren gehen - nur der eine Stream, diese eine Kette pausieren und darauf warten muss, dass die fehlende Verbindung wieder versendet wird. 

Hier wird dies mit einem gelben und einem blauen Stream illustriert, die zwischen zwei Endpunkten versendet werden.

![Zwei QUIC Streams zwischen zwei Computern](../images/quic-chain-streams.png)
