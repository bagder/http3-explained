## Transport and application level

The IETF QUIC protocol is a transport protocol, on top of which other
application protocols can be used. The initial application layer protocol is
HTTP/3 (h3).

The transport-layer does connections and streams.

The legacy Google version of QUIC had transport and HTTP glued together into
one single do-it-all and was a more special-purpose
send-http/2-frames-over-udp protocol
