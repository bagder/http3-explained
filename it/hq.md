# HTTP over QUIC

As mentioned previously in this document, the first and primary protocol to
transport over QUIC is HTTP.

Much like HTTP/2 was once introduced to transport HTTP over the wire in a
compltely new way, QUIC is yet again introducing a new way to send HTTP over
the network.

HTTP still maintains the same paradigms and concepts like before. There are
headers and a body, there's a request and a response. There are verbs, cookies
and caching. What primarily changes with HTTP over QUIC (hq) is how the bits
gets sent over to the other side of the communication.
