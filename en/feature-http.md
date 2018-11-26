## HTTP/3

The HTTP layer does HTTP-style transports, including HTTP header compression
using QPACK - which is very similar to the HTTP/2 compression named HPACK.

The HPACK algorithm depends on an *ordered* delivery of streams so it was not
possible to reuse that for HTTP/3 without modifications since QUIC offers
streams that can be delivered out of order. QPACK can be seen as the
QUIC-adapted version of [HPACK](http://httpwg.org/specs/rfc7541.html).

