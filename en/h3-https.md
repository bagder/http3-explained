# HTTPS:// URLs

HTTP/3 will be performed using `HTTPS://` URLs. The world is full of these
URLs and it has been deemed impractical and downright unreasonable to
introduce another URL scheme for the new protocol. Much like HTTP/2 did not
need a new scheme, neither will HTTP/3.

The added complexity in the HTTP/3 situation is however that where HTTP/2 was
a completely new way of transporting HTTP over the wire, it was still based on
TLS and TCP like HTTP/1 was. The fact that HTTP/3 is done over QUIC changes
things in a few important aspects.

Legacy, clear-text, `HTTP://` URLs will be left as-is and as we proceed
further into a future with more secure transfers they will probably become
less and less frequently used. Requests to such URLs will simply not be
upgraded to use HTTP/3. In reality they very rarely upgrade to HTTP/2 either,
but for other reasons.

## Initial connection

The first connection to a fresh, not previously visited-before, host for a
HTTPS:// URL probably has to be done over TCP (possibly in addition to a
parallel attempt to connect QUIC). The host might be a legacy server without
QUIC support or there might be a middle box in between setting up obstacles to
succeed with a QUIC connection.

A modern client and server would presumably negotiate HTTP/2 in the first
handshake. When the connection has been setup and the server responds to a
client HTTP request, the server can tell the client about its support of and
preference for HTTP/3...
