<!--
## ‎Multiple streams within connections

Similar to SCTP, SSH and HTTP/2, QUIC features separate logical streams within
the physical connections. A number of parallel streams that can transfer data
simultaneously over a single connection without affecting the other streams.

A connection is a negotiated setup between two end-points similar to how a TCP
connection works. A QUIC connection is made to a UDP port and IP address, but
once established the connection is associated by its "connection ID".

Over an established connection, either side can create streams and send data
to the other end. Streams are delivered in-order and they are reliable, but
different streams may be delivered out-of-order.

QUIC offers flow control on both connection and streams.

See further details in [connections](quic-connections.md) and
[streams](quic-streams.md) sections
-->

## 연결 내의 다중 스트림

QUIC은 SCTP, SSH, HTTP/2와 마찬가지로 물리 연결 내에서 논리적 스트림을 나눌 수 있다.
하나의 연결로 다수의 병렬 스트림으로 다른 스트림에 영향을 주지 않고 데이터를 동시에 전송할 수 있다.

두 엔드포인트 사이에 연결 협상이 이뤄지는 방식은 TCP 연결이 동작하는 방식과 비슷하다. QUIC 연결은
UDP 포트와 IP 주소로 이루어져 있지만 일단 연결을 만들고 나면 "connection ID"로 연결된다.

만들어진 연결을 통해 양쪽에서 스트림을 만들어 다른 쪽으로 데이터를 보낼 수 있다. 스트림은 순서대로
전달되고 신뢰할 수 있지만 서로 다른 스트림은 순서 없이 전달될 수 있다.

QUIC은 연결과 스트림 모두에서 흐름 제어를 제공한다.

더 자세한 내용은 [연결](quic-connections.md)과 [스트림](quic-streams.md) 부분을 참고하라.
