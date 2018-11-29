# Connections use TLS

Immediately after the initial packet setting up a connection, the initiator
sends a crypto frame that starts setting up the secure layer handshake. The
security layer uses TLS 1.3 security.

There is no way to opt-out or avoid using TLS for a QUIC connection. The
protocol is designed to be hard for middle-boxes to tamper with, in order
to help prevent ossification of the protocol.
