## TCP or UDP

If we can't fix head-of-line blocking within TCP, then in theory we should
be able to make a new transport protocol next to UDP and TCP in the network
stack. Or perhaps even use
[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol)
which is a transport protocol standardized by the IETF in [RFC
4960](https://tools.ietf.org/html/rfc4960) with several of the desired
characteristics.

However, in recent years efforts to create new transport protocols have almost
entirely been halted because of the difficulties in deploying them on the Internet. 
Deployment of new protocols is hampered by many firewalls, NATs, routers and other 
middle-boxes that only allow TCP or UDP are deployed between users and the servers 
they need to reach. Introducing another transport protocol makes N% of the connections
fail because they are being blocked by boxes that see it not being UDP or TCP and 
thus evil or wrong somehow. The N% failure rate is often deemed too high to be 
worth the effort.

Additionally, changing things in the transport protocol layer of the network
stack typically means protocols implemented by operating system kernels.
Updating and deploying new operating system kernels is a slow process that
requires significant effort. Many TCP improvements standardized by the IETF
are not widely deployed or used because they are not broadly supported.

## Why not SCTP-over-UDP

SCTP is a reliable transport protocol with streams, and for WebRTC there are
even existing implementations using it over UDP.

This was not deemed good enough as a QUIC alternative due to several reasons,
including:

 - SCTP does not fix the head-of-line-blocking problem for streams
 - SCTP requires the number of streams to be decided at connection setup
 - SCTP does not have a solid TLS/security story
 - SCTP has a 4-way handshake, QUIC offers 0-RTT
 - QUIC is a bytestream like TCP, SCTP is message-based
 - QUIC connections can migrate between IP addresses but SCTP cannot

For more details on the differences, see [A Comparison between SCTP and
QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).
