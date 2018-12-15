## ‎Reliable data transfers

While UDP is not a reliable transport, QUIC adds a layer on top of UDP that
introduces reliability. It offers re-transmissions of packets, congestion
control, pacing and the other features otherwise present in TCP.

Data sent over QUIC from one end-point will appear in the other end sooner or
later, as long as the connection is maintained.
