## TCP or UDP

If we can't fix the head of line blocking within TCP, then in theory we should
be able to make a new transport protocol next to UDP and TCP in the network
stack. Or perhaps even use
[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol)
which is a transport protocol standardized by the IETF in [RFC
4960](https://tools.ietf.org/html/rfc4960) with several of the desired
characteristics.

However, in recent years efforts to create new transport protocols have almost
entirely been halted because of the perceived difficulties to deploy them for
real on the Internet. The amount of firewalls, NATs, routers and other
middle-boxes that exist between users and the servers that only know of and
let TCP or UDP through is quite simply too many. Introducing another transport
protocol makes N% of the connections fail because they are being blocked by
boxes that see it not being UDP or TCP and thus evil or wrong somehow. The N%
failure rate is often deemed too high to be worth the effort.

Additionally, changing things in the transport protocol layer of the network
stack typically means protocols implemented by operating system kernels.
Changing operating system kernels is a very slow process that takes its own
efforts and pushes. In recent years we have seen TCP features get standardized
by the IETF and yet after many years they are still not widely deployed or
used because they are not supported widely enough yet.

## Why not SCTP-over-UDP

SCTP is a reliable transport protocol with streams, and for WebRTC there are
even existing implementations doing it over UDP.

This was not deemed good enough as a QUIC alternative due to several reasons,
including...

 - SCTP doesn't fix the head-of-line-blocking problem for streams
 - SCTP requires the number of streams to be decided at connection setup
 - SCTP does not have a solid TLS/security story
 - SCTP has a 4-way handshake, QUIC offers 0-RTT
 - QUIC is a bytestream like TCP, SCTP is message-based
 - QUIC can move between IP addresses as SCTP can't

For more details on the differences, the [A Comparison between SCTP and
QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00)
internet draft is helpful.
