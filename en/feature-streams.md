## Multiple streams within connections

Similar to SCTP, SSH and HTTP/2, QUIC features separate logical streams within
the physical connections. A number of parallel streams that can transfer data
simultaneously over a single connection without affecting the other streams.

A connection is a negotiated setup between two end-points similar to how a TCP
connection works. A QUIC connection is made to a UDP port and IP address, but
once established the connection is associated by its "connection ID".

Over an established connection, either side can create streams and send data
to the other end. Streams are delivered in-order and they are reliable, but
different streams may be delivered out-of-order.

QUIC offers flow control on both connection and streams.

See further details in [connections](quic-connections.md) and
[streams](quic-streams.md) sections
