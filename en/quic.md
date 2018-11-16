# How QUIC works

Without explaining the exact bits and bytes on the wire, this section intends
to describe how the fundamental building blocks of the QUIC transport protocol
works. If you want to implement your own QUIC stack, this description should
give you an understanding but for all the details we refer to the actual IETF
internet drafs and RFCs.

1. Setup a [connection](quic-connections.md)
2. ... that includes [TLS security](quic-tls.md)
3. Then use [streams](quic-streams.md)
