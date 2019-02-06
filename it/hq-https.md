# HTTPS:// URLs

HTTP over QUIC will be performed using `HTTPS://` URLs. The world is full of
these URLs and it has been deemed impractical and downright unreasonable to
introduce another URL scheme for the new protocol. Much like HTTP/2 didn't
need a new scheme, neither will QUIC.

The added challenge in the QUIC situation is however that where HTTP/2 was a
completely new way of transporting HTTP over the wire, it was still based on
TLS and TCP like HTTP/1 was. The fact that QUIC is done over UDP changes
things in a few important aspects.

Legacy, clear-text, `HTTP://` URLs will be left as-is and as we proceed
further into a future with more secure transfers they will probably become
less frequently used. Requests to such URLs will not be upgraded to use
QUIC. In reality they very rarely upgrade to HTTP/2 either, but for other
reasons.

## Initial connection

The first connection to a fresh, not preciously visited-before, host for a
HTTPS:// URL probably has to be done over TCP (possibly in addition to a
parallel attempt to connect QUIC). The host might be a legacy server without
QUIC support. A modern client and server would presumably negotiate HTTP/2 in
that first handshake.

When the connection has been setup and the server responds to a client
request, the server can tell the client about its support of QUIC...
