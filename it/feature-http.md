## HTTP/3

Il layer HTTP si occupa dei trasporti in stile HTTP, inclusa la compressione
degli header utilizzando QPACK - simile alla compressione usata in ambito
HTTP/2, detta HPACK.

L'algoritmo HPACK si basa sulla consegna *ordinata* dei flussi quindi non è
stato possibile riciclarlo per HTTP/3 senza apportarvi modifiche, visto che
QUIC permette la consegna di flussi al di fuori dell'ordine predefinito.
QPACK può essere visto come una versione di [HPACK
](https://httpwg.org/specs/rfc7541.html) adattata su misura per QUIC.
