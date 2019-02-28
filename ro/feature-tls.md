## TLS 1.3

Securitatea transferurilor în QUIC este implementată folosing TLS 1.3 ([RFC
8446](https://tools.ietf.org/html/rfc8446)) și nu există conexiuni QUIC 
necriptate.

TLS 1.3 are câteva avantaje asupra versiunilor mai vechi de TLS, dar un motiv 
principal de a-l folosi în QUIC a fost că versiunea 1.3 a micșorat numărul de 
handshakes necesare. Asta reduce timpii de încărcare ai protocolului.

Vechea versiune QUIC de la Google folosea un algoritm propriu de criptare.
