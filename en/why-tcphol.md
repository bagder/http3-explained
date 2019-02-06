## TCP head of line blocking

HTTP/2 is done over TCP and with much fewer TCP connections than when using
earlier HTTP versions. TCP is a protocol for reliable transfers and you can
basically think of it as an imaginary chain between two machines. What is
being put out on the network in one end will end up in the other end, in the
same order - eventually. (Or the connection breaks.)

![a TCP chain between two computers](../images/tcp-chain.png)

With HTTP/2, typical browsers do tens or hundreds of parallel transfers over
a single TCP connection.

If a single packet is dropped, or lost in the network somewhere between two
endpoints that speak HTTP/2, it means the entire TCP connection is brought to
a halt while the lost packet is re-transmitted and finds its way to
the destination. Since TCP is this "chain", it means that if one link is
suddenly missing, everything that would come after the lost link needs to
wait.

An illustration using the chain metaphor when sending two streams over this
connection. A red stream and a green stream:

![the chain showing links in different colors](../images/tcp-chain-streams.png)

It becomes a TCP-based head of line block!

As the packet loss rate increases, HTTP/2 performs less and less well. At 2%
packet loss (which is a terrible network quality, mind you), tests have proven
that HTTP/1 users are usually better off - because they typically have up to 
six TCP connections to distribute lost packets over. This means for every lost 
packet the other connections can still continue.

Fixing this issue is not easy, if at all possible, with TCP.

## Independent streams avoids the block

With QUIC there is still a connection setup between the two end-points that
makes the connection secure and the data delivery reliable.

![a QUIC chain between two computers](../images/tcp-chain.png)

When setting up two different streams over this connection, they are treated
independently so that if any link goes missing for one of the streams, only
that stream, that particular chain, has to pause and wait for the missing link
to get retransmitted.

Illustrated here with one yellow and one blue stream sent between two
end-points.

![two QUIC streams between two computers](../images/quic-chain-streams.png)
