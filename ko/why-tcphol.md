<!--
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
-->

## TCP HOL(head of line) 블로킹

HTTP/2는 TCP를 사용하며 이전 HTTP 버전을 사용할 때 보다 더 적은 TCP 연결을 사용한다. TCP는
신뢰할 수 있는 전송 프로토콜이고 기본적으로 두 머신 간의 가상 체인으로 생각해도 된다. 네트워크의 한쪽
끝에 넣은 것이 최종적으로 다른 쪽 끝에 같은 순서로 나올 것이다.(아니면 연결이 끊어진다.)

![두 컴퓨터 사이의 TCP 체인](../images/tcp-chain.png)

HTTP/2를 사용하는 일반적인 브라우저는 TCP 연결 한개로 수십, 수백 개의 병렬 전송을 한다.

HTTP/2로 통신하는 두 엔드포인트 사이 네트워크 어딘가에서 하나의 패킷이 빠지거나 없어진다면
없어진 패킷을 다시 전송하고 목적지를 찾는 동안 전체 TCP 연결이 중단되게 된다.
즉, TCP는 "체인"이기 때문에 한 링크가 갑자기 사라지면 그 링크 이후에 와야 하는 모든 것들이 기다려야
한다는 뜻이다.

체인 메타포를 사용해서 이 연결을 통해 두 스트림을 보내는 경우를 그린 그림을 보자.
빨간색 스트림과 녹색 스트림이 있다.

![체인에서 링크는 다른 색으로 보여준다](../images/tcp-chain-streams.png)

이는 TCP에 기반을 둔 head of line 블로킹이 된다!

패킷 손실률이 증가하면 HTTP/2의 성능도 저하된다. 테스트를 통해 패킷 손실률이 2%(상기하자면, 이는 끔찍한
네트워크 품질이다) 일때 HTTP/1 사용자가 더 나은 것으로 입증했다. 그 이유는 HTTP/1은 보통 손실된 패킷을
분배하는데 6개의 TCP 연결을 갖고 있어서 손실된 패킷이 없는 다른 연결은 계속 사용할 수 있기 때문이다.

TCP를 사용하는 한 이 이슈를 고치는 것은 (가능할 수도 있지만) 쉽지 않다.

## 차단을 피하는 독립 스트림

QUIC에는 두 엔드포인트간에 연결을 안전하게 하고 데이터 전달을 신뢰할 수 있게 하는 연결 설정이 있다.

![두 컴퓨터 사이의 QUIC 체인](../images/tcp-chain.png)

이 연결을 통해 두 가지 다른 스트림을 설정했을 때 이들을 독립적으로 다루므로 스트림 중 하나에서
어떤 링크가 사라지더라도 해당 스트림만(특정 체인) 멈추고 재전송될 없어진 링크를 기다란다.

다음은 두 엔드포인트간에 노란색과 파란색 스트림을 보내는 그림이다.

![두 컴퓨터 사이의 두 가지 QUIC 스트림](../images/quic-chain-streams.png)
