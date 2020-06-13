# Criticism

## UDP will never work

A lot of enterprises, operators and organizations block or rate-limit UDP
traffic outside of port 53 (used for DNS) since it has in recent days mostly
been abused for attacks. In particular, some of the existing UDP protocols and
popular server implementations for them have been vulnerable for amplification
attacks where one attacker can make a huge amount of outgoing traffic to
target innocent victims.

QUIC has built-in mitigation against amplification attacks by requiring that the
initial packet must be at least 1200 bytes and by restriction in the protocol
that says that a server must not send more than three times the size of the
request in response without receiving a packet from the client in response.

## UDP is slow in kernels

This seems to be the truth, at least initially. We can of course not tell
how this will develop and how much of this is simply the result of UDP
transfer performance not having been in developers' focus for many years.

For most clients, this "slowness" is probably never even noticeable.

## QUIC takes too much CPU

Similar to the "UDP is slow" remark above, this is partly because the TCP and
TLS usage of the world has had a longer time to mature, improve and get
hardware assistance.

There are reasons to expect this to improve over time, and already [we are seeing
some improvements in this space](https://www.fastly.com/blog/measuring-quic-vs-tcp-computational-efficiency).
The question is how much this extra CPU usage will hurt deployers.

## This is just Google

No it is not. Google brought the initial spec to the IETF after having proved,
on a large Internet-wide scale, that deploying this style of protocol over UDP
actually works and performs well.

Since then, individuals from a large number of companies and organizations
have worked in the vendor-neutral organization IETF to put together a standard
transport protocol out of it. In that work, Google employees have of course
been participating, but so have employees from a large number of other
companies that are interested in furthering the state of transport protocols
on the Internet, including Mozilla, Fastly, Cloudflare, Akamai, Microsoft,
Facebook and Apple.

## This is too small of an improvement

That is not really a critique but an opinion. Maybe it is, and maybe it is too
little of an improvement so close in time since HTTP/2 was shipped.

HTTP/3 is likely to perform much better in packet loss-ridden networks, it
offers faster handshakes so it will improve latency both as perceived and
actual. But is that enough of benefits to motivate people to deploy HTTP/3
support on their servers and for their services? Time and future performance
measurements will surely tell!
