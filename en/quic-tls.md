# Connections use TLS

Immediately after the initial packet setting up a connection, the initiator
send a crypto frame that starts setting up the secure layer handshake. The
sercurity layer is using TLS 1.3 security.

There is no way to opt-out or avoid using TLS for a QUIC connection and the
protocol makes an effort to do the protocol in a way that makes it hard to
tamper with for middleboxes.
