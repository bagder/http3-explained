<!--
# Fast handshakes

QUIC offers both 0-RTT and 1-RTT connection setups, meaning that at best QUIC
needs no extra round-trips at all when setting up a new connection. The faster
of those two, the 0-RTT handshake, only works if there has been a previous
connection established to a host and a secret from that connection has been
cached.

## Early data

QUIC allows a client to include data already in the 0-RTT handshake. This
feature allows a client to deliver data to the peer as fast as it possibly
can, and that then of course allows the server to respond and send data back
even sooner.
-->

# 빠른 핸드쉐이크

QUIC은 0-RTT와 1-RTT 연결 설정을 둘 다 지원하므로 새로운 연결을 설정할 때 추가적인 라운드 트립이
전혀 필요치 않다. 둘 중 더 빠른 0-RTT 핸드쉐이크는 호스트에 이전 연결이 구성되어 있고
해당 연결의 시크릿이 캐시 되어 있을 때만 동작한다.

## 초기 데이터

QUIC은 0-RTT 핸드쉐이크에 이미 있는 데이터를 클라이언트가 포함할 수 있게 한다. 이 기능으로
데이터를 피어에 최대한 빨리 전달할 수 있으므로 서버가 더 빨리 응답하고 데이터를 돌려줄 수 있다.
