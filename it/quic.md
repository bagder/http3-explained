# How QUIC works

Without explaining the exact bits and bytes on the wire, this section describes how
the fundamental building blocks of the QUIC transport protocol work. If you want to
implement your own QUIC stack, this description should give you a general
understanding, but for all the details, refer to the actual IETF Internet Drafts
and RFCs.

1. Set up a [connection](quic-connections.md)
2. ... that includes [TLS security](quic-tls.md)
3. Then use [streams](quic-streams.md)
