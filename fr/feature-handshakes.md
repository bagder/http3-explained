# Fast handshakes

QUIC offers both 0-RTT and 1-RTT connection setups, meaning that at best QUIC
needs no extra round-trips at all when setting up a new connection. The faster
of those two, the 0-RTT handshake, only works if there has been a previous
connection established to a host and a secret from that connection has been
cached.

## Early data

QUIC allows a client to include data already in the 0-RTT handshake. This
feature allows a client to deliver data to the peer as fast as it possibly
can, and that then of course allows the server to respond and send data back
even sooner.
