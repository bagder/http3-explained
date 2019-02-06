## Secure

QUIC is always secure. There is no clear-text version of the protocol so to
negotiate a QUIC connection means doing cryptography and security with TLS
1.3. As mentioned above, this prevents ossification as well as other sorts of
blocks and special treatments, as well as making sure QUIC has all the secure
properties of HTTPS that web users have come to expect and want.

There are only a few initial handshake packets that are sent in the clear
before the encryption protocols have been negotiated.
