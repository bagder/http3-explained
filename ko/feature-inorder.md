<!--
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
-->

## 순서에 맞는 전송

QUIC은 스트림의 순서 있는 전송을 보장하지만 스트림 사이에서는 (순서를) 보장하지 않는다. 스트림은
순서대로 데이터를 전송하고 유지하지만, 각 스트림은 애플리케이션이 보낸 것과는 다른 순서대로 목적지에 
도착할 수 있다!

스트림 A와 B가 서버에서 클라이언트로 이동하는 예를 생각해 보자. 스트림 A를 먼저 시작하고 이어서
스트림 B를 시작했다. QUIC에서 잃어버린 패킷은 해당 패킷이 속한 스트림에만 영향을 준다. 스트림 A는
패킷을 잃어버렸지만 스트림 B는 잃어버리지 않았다면 스트림 A의 잃어버린 패킷을 다시 전송하는 동안
스트림 B는 계속해서 전송하면서 완료될 수 있다. 이는 HTTP/2에서는 불가능했다.

다음은 하나의 연결을 통해 두 QUIC 앤드포인트 사이에 보내진 노란색 스트림과 파란색 스트림의 그림이다.
이 두 스트림은 독립적이고 다른 순서로 도착할 것이지만 각 스트림은 신뢰할 수 있게
애플리케이션에 순서대로 전달된다.

![두 컴퓨터 사이에 두 QUIC 스트림](../images/quic-chain-streams.png)
