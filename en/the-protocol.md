# The QUIC protocol

The protocol from a high level.

(Insert schematic picture of the protocol architecture, possibly compared to
HTTP/2)

## Transfer protocol over UDP

QUIC is a custom transfer protocol, implement in user-space, on top of UDP. If
you watch your network traffic casually, you'll see QUIC appear as UDP
packets.

## ‎Reliable data transfers

While UDP is not a reliable transport, QUIC adds a layer on top of UDP that
introduces reliability. It offers retransmissions of packets, congestion
control, pacing and the other features otherwise present in TCP.

Data sent over QUIC from one end-point will appear in the other end sooner or
later, as long as the connection is maintained.

(Insert discussion about unreliable streams.)

## ‎Multiple streams within connections

Similar to SCTP, SSH and HTTP/2, QUIC features separate logical streams within
the physical connections. A number of parallel streams that can transfer data
simultaneously without affecting the other strams.

## ‎In order delivery

QUIC guarantees in-order delivery of streams, but not between-streams. This
means that each stream will send data and maintain data order, but each stream
may reach the destination in a different order than what the application sent
them at the sending side!

For example: stream A and B are transferred from a server to a client. Stream
A is started first and then stream B. In QUIC, a lost packet would only affect
the stream(s) to which the lost packet belongs. If stream A gets a packet
lost, and stream B does not, stream B may continue its tranfers and complete
while stream A is getting its lost packet retransmitted. This was not possible
with HTTP/2.

## ‎TLS 1.3

The transport security used in QUIC is using TLS 1.3. The Google version of
QUIC used a custom approach.

## Transport and application level

The IETF protocol is two-layered. There's a transport QUIC and an
application-level QUIC. The initial application layer will be HTTP over QUIC
(hq).

The transport-layer does connections and streams.

## HTTP over QUIC

The HTTP layer does HTTP-style transports, including HTTP header compression
using QPACK. The HTTP/2 compression algorithm depends on an ordered delivery
of streams so it wasn't possible to reuse that for QUIC with a certain amount
of modifications. QPACK can be seen as the QUIC-adapted version of
[HPACK](http://httpwg.org/specs/rfc7541.html).

## Non-HTTP over QUIC

The work on sending other protocols than HTTP over QUIC has been postponed to
be worked on after QUIC version 1 has shipped.

## ‎Congestion control

TBD
