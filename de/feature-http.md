## HTTP/3 über QUIC

Die HTTP-Schicht namens HTTP/3 führt Transporte im HTTP-Stil durch, einschließlich HTTP-Header-Komprimierung mit QPACK - ähnlich der HTTP/2-Komprimierung HPACK.

Der HPACK-Algorithmus hängt von einer *geordneten* Übermittlung von Streams ab, weshalb es nicht möglich war, ihn ohne Änderungen in HTTP/3 wiederzuverwenden; vor allem, weil QUIC Streams anbietet, die nicht in der richtigen Reihenfolge übermittelt werden können. QPACK kann als die QUIC-angepasste Version von [HPACK](https://httpwg.org/specs/rfc7541.html) gesehen werden.
