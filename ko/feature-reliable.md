<!--
## ‎Reliable data transfers

While UDP is not a reliable transport, QUIC adds a layer on top of UDP that
introduces reliability. It offers re-transmissions of packets, congestion
control, pacing and the other features otherwise present in TCP.

Data sent over QUIC from one end-point will appear in the other end sooner or
later, as long as the connection is maintained.
-->

## 신뢰할 수 있는 데이터 전송

UDP가 데이터 전송의 신뢰성을 보장하지 않지만, QUIC은 UDP 위에 새로운 계층을 추가함으로써 신뢰성을 제공한다. 
추가된 계층은 TCP에 존재하는 패킷 재전송, 혼잡 제어, 속도 조정 및 다른 기능들을 제공한다.

한 엔드포인트로부터 QUIC을 통해 전송된 데이터는 연결이 유지되는 한 다른 엔드포인트에서 수신할 수 있다.