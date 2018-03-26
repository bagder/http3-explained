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
middle-boxes that exist betweeen users and the servers that only know of and
let TCP or UDP through is quite simply too many. Introducind another transport
protocol makes N% of the connections fail because they are being blocked by
boxes that see it not being UDP or TCP and thus evil or wrong somehow. The N%
failure rate is often deemed too high to be worth the effort.

Additionally, changing things in the transport protocol layer of the network
stack typically means protocols implemented by operating system kernels.
Changing operating system kernels is a very slow process that takes its own
efforts and pushes. In recent years we have seen TCP features get standardized
by the IETF and yet after many years they are still not widely deployed or
used because they are not supported widely enough yet.
