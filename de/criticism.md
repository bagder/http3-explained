#Kritik

## UDP wird nie funktionieren

Viele Unternehmen, Betreiber und Organisationen blockieren oder begrenzen den UDP
Verkehr außerhalb des Ports 53 (der für DNS verwendet wird), da dieser in den letzten Tagen meist
für Angriffe missbraucht wurde. Insbesondere einige der bestehenden UDP-Protokolle und
populären Server-Implementierungen für diese sind anfällig für Amplifikationsangriffe, 
bei denen ein Angreifer eine riesige Menge an ausgehendem Verkehr erzeugen kann, um
unschuldige Opfer anzugreifen.

QUIC verfügt über eine eingebaute Abschwächung gegen Amplifikationsangriffe, indem es vorschreibt, dass das
erste Paket mindestens 1200 Bytes groß sein muss und durch eine Einschränkung im Protokoll
die besagt, dass ein Server nicht mehr als die dreifache Größe der
Anfrage als Antwort senden darf, ohne ein Paket vom Client als Antwort zu erhalten.

## UDP ist langsam im Kernel

Dies scheint die Wahrheit zu sein, zumindest anfangs. Wir können natürlich nicht sagen, wie 
sich das entwickeln wird und wie viel davon einfach das Ergebnis davon ist, dass die UDP
Übertragungsleistung seit vielen Jahren nicht mehr im Fokus der Entwickler stand.

Für die meisten Clients ist diese "Langsamkeit" wahrscheinlich nicht einmal spürbar.

## QUIC braucht zu viel CPU

Ähnlich wie bei der "UDP ist langsam" Bemerkung oben, liegt dies teilweise daran, dass die TCP- und
TLS-Nutzung der Welt eine längere Zeit hatte, um zu reifen, sich zu verbessern und
Hardware-Unterstützung zu bekommen.

Es gibt Gründe zu erwarten, dass sich dies im Laufe der Zeit verbessern wird, und [wir sehen bereits
einige Verbesserungen in diesem Bereich](https://www.fastly.com/blog/measuring-quic-vs-tcp-computational-efficiency).
Die Frage ist, wie sehr diese zusätzliche CPU-Belastung den Bereitstellern schaden wird.

## Das ist nur Google

Nein, ist es nicht. Google brachte die ursprüngliche Spezifikation in die IETF ein, nachdem es bewiesen hatte,
dass der Einsatz dieser Art von Protokoll über UDP tatsächlich funktioniert und gut performt.

Seitdem haben Personen aus einer großen Anzahl von Unternehmen und Organisationen
in der Hersteller-neutralen Organisation IETF daran gearbeitet, ein Standard
Transportprotokoll daraus zu machen. An dieser Arbeit haben sich natürlich auch Mitarbeiter von Google
beteiligt, aber auch Mitarbeiter einer großen Anzahl anderer Unternehmen, die daran interessiert sind, 
den Zustand der Transportprotokolle im Internet zu fördern, darunter Mozilla, Fastly, Cloudflare, Akamai, Microsoft,
Facebook und Apple.

## Das ist eine zu geringe Verbesserung

Das ist nicht wirklich eine Kritik, sondern eine Meinung. Vielleicht ist es das, und vielleicht ist es
eine zu geringe Verbesserung so kurz nach der Auslieferung von HTTP/2.

HTTP/3 wird wahrscheinlich in Paket-verlustbehafteten Netzwerken viel besser funktionieren, es
bietet schnellere Handshakes, sodass es die gefühlte und tatsächliche Latenzzeit verbessert.
Aber ist das genug an Vorteilen, um Leute zu motivieren, HTTP/3 Unterstützung auf ihren Servern 
und für ihre Dienste einzusetzen? Die Zeit und zukünftige Leistungsmessungen werden es sicherlich zeigen!
