## TLS 1.3

The transport security used in QUIC is using TLS 1.3 ([RFC
8446](https://tools.ietf.org/html/rfc8446)) and there is never any unencrypted
QUIC connections.

TLS 1.3 has several advantages compared to older TLS versions but a primary
reason for using it in QUIC is that 1.3 changed the handshake to require fewer
roundtrips. It reduces protocol latency.

The Google legacy version of QUIC used a custom crypto.
