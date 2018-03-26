## TCP head of line blocking

HTTP/2 however is still done over TCP and even with much fewer TCP connections
than before. TCP is a protocol for reliable transfers and you can basically
think of it as an imaginary string between two machines. What is being put out
on the network in one end will end up in the other end, in the same order -
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

