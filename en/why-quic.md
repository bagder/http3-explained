# Why QUIC

The abbreviation QUIC is said to stand for "Quick UDP Internet Connections"
and is pronounced exactly like the English work "quick".

QUIC is in many ways what could be seen as "HTTP/3", the logical next step in
the web transport evolution, but it isn't just limited to transporting
HTTP. The desire to make the web and data in general delivered faster to end
users is probably the largest reason and push that initially triggered the
creation of this protocol.

So why create a new transport protocol and why do it on top of UDP?

## Remember HTTP/2?

The HTTP/2 specification RFC 7540 was published in May 2015 and the protocol
has since then been implemented and deployed widely across the Internet and
the world wide web.

HTTP/2 adresses a whole slew of shortcomings in HTTP/1 and with the
introduction of the second version of HTTP users can stop using a bunch of
work-arounds. Some of which are pretty burdonsome on web developers.

One of the primary features of HTTP/2 is that it makes use of multiplexing, so
that many logical streams are sent over the same physical TCP connection. This
makes a lot of things better and faster. It make congestion control work much
better, it let's users use TCP much better and thus properly saturate the
bandwidth, makes the TCP connections more long-lived - which is good so that
they get up to full speed more frequently than before. Header compression
makes it use less bandwidth.

With HTTP/2, browsers typically use *one* TCP connection to each host instead
of the previous *six*. In fact, connection coalescing and "desharding"
techniques used with HTTP/2 may actually even reduce the number of connections
much more than so.

With HTTP/2, the HTTP head of line blocking problem was "fixed". The problem
that clients had to wait for the request before in the line to finish before
the next one could go out.

## TCP head of line blocking

HTTP/2 however is still done over TCP and even with much fewer TCP connections
than before. TCP is protocol for reliable transfers and you can basically
think of it as a string between two machines. What is being put out on the
network in one end will end up in the other end, in the same order -
eventually. (Or the connection breaks.)

With HTTP/2, typical browsers do tens or hundreds of parallel transfers over
that single TCP connection.

If a single packet is dropped, lost, in the network somewhere between two
endpoints that speak HTTP/2, it means the entire TCP connection is brought to
a halt while the lost packet needs to be retransmitted and find its way to the
destination. Since TCP is this "string", it means everything that would come
after the lost packet needs to wait.

It becomes a TCP head of line block.

As the packet loss rate increases, HTTP/2 performs less and less good. At 2%
packet loss (which is a terrible network quality, mind you), tests have proven
that HTTP/1 users are usually better off - because they typically have six TCP
connections up to distribute the lost packet over so for each lost packet the
other connections without loss can still continue.

Fixing this issue is not easy, if at all possible, to do with TCP.

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
protocol makes N% of the connections fail because they're being blocked by
boxes that see it not being UDP or TCP and thus evil or wrong somehow. The N%
failure rate is often deemed too high to be worth the effort.

Additionally, changing things in the transport protocol layer of the network
stack typically means protocols implemented by operating system kernels.
Changing operating system kernels is a very slow process that takes its own
efforts and pushes. In recent years we've seen TCP features get standardized
by the IETF and yet after many years they're still not widely deployed or used
because they're not supported widely enough yet.

## Ossification

Changes to TCP also suffers from the middle-box problem, in that some of the
boxes will spot new TCP options and block such connections since they don't
know what the options are. That's called "protocol ossification". If allowed
to spot protocol details, systems learn how protocols behave and the over time
it is impossible to change them.

The only really effective way to "combat" ossification, is to encrypt as much
as possible of the communcation to prevent middle-boxes to see much of the
protocol passing through.

## Always secure

QUIC is always secure. There's no clear-text version of the protocol so to
negotiate a QUIC connection means doing cryptography and security with TLS
1.3. As mentioned above, this prevents ossification as well as other sort of
blocks and special treatments, as well as making sure QUIC has all the secure
properties of HTTPS that web users have come to expect and want.

## Earlier data

QUIC offers both a 0-RTT and 1-RTT handshakes that reduces the time it takes
to negotiate a new connection, to be compared with the 3-way handshake of TCP.

In addition to that, QUIC offers "early data" support from the get go which is
done to allow more data and it is used more easily than TCP Fast Open. (insert
horror-stories from Firefox TFO agonies?)

## User-space

Implementing a transport protocol in user-space helped driving the development
and the quick interations of the protocol since it was "easy" for Google to
run it in both ends of their operations and have users take advantage of new
development very frequently.
