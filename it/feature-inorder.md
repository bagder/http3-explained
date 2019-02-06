## ‎In order delivery

QUIC guarantees in-order delivery of streams, but not between streams. This
means that each stream will send data and maintain data order, but each stream
may reach the destination in a different order than the application sent it!

For example: stream A and B are transferred from a server to a client. Stream
A is started first and then stream B. In QUIC, a lost packet only affects
the stream to which the lost packet belongs. If stream A loses a packet but
stream B does not, stream B may continue its transfers and complete
while stream A's lost packet is re-transmitted. This was not possible
with HTTP/2.

Illustrated here with one yellow and one blue stream sent between two QUIC
end-points over a single connection. They are independent and may arrive in a
different order, but each stream is reliably delivered to the application in order.

![two QUIC streams between two computers](../images/quic-chain-streams.png)
