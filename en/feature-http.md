## HTTP over QUIC

The HTTP layer does HTTP-style transports, including HTTP header compression
using QPACK. The HTTP/2 compression algorithm depends on an ordered delivery
of streams so it wasn't possible to reuse that for QUIC with a certain amount
of modifications. QPACK can be seen as the QUIC-adapted version of
[HPACK](http://httpwg.org/specs/rfc7541.html).

