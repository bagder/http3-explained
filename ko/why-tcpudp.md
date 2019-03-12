<!--
## TCP or UDP

If we can't fix head-of-line blocking within TCP, then in theory we should
be able to make a new transport protocol next to UDP and TCP in the network
[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol)
which is a transport protocol standardized by the IETF in [RFC
4960](https://tools.ietf.org/html/rfc4960) with several of the desired
characteristics.

However, in recent years efforts to create new transport protocols have almost
entirely been halted because of the difficulties in deploying them on the Internet.
Deployment of new protocols is hampered by many firewalls, NATs, routers and other
middle-boxes that only allow TCP or UDP are deployed between users and the servers
they need to reach. Introducing another transport protocol makes N% of the connections
fail because they are being blocked by boxes that see it not being UDP or TCP and
thus evil or wrong somehow. The N% failure rate is often deemed too high to be
worth the effort.

Additionally, changing things in the transport protocol layer of the network
stack typically means protocols implemented by operating system kernels.
Updating and deploying new operating system kernels is a slow process that
requires significant effort. Many TCP improvements standardized by the IETF
are not widely deployed or used because they are not broadly supported.

## Why not SCTP-over-UDP

SCTP is a reliable transport protocol with streams, and for WebRTC there are
even existing implementations using it over UDP.

This was not deemed good enough as a QUIC alternative due to several reasons,
including:

 - SCTP does not fix the head-of-line-blocking problem for streams
 - SCTP requires the number of streams to be decided at connection setup
 - SCTP does not have a solid TLS/security story
 - SCTP has a 4-way handshake, QUIC offers 0-RTT
 - QUIC is a bytestream like TCP, SCTP is message-based
 - QUIC connections can migrate between IP addresses but SCTP cannot

For more details on the differences, see [A Comparison between SCTP and
QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).
-->

## TCP 혹은 UDP

TCP에서 head-of-line 블로킹을 해결할 수 없다면 이론적으로 네트워크 스택에서 UDP와 TCP 옆에
새로운 전송 프로토콜을 만들 수 있다. 아니면
[RFC 4960](https://tools.ietf.org/html/rfc4960)에서 IETF가 표준화하고 여러 가지
원하는 특성이 있는 전송 프로토콜인
[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol)를
사용할 수도 있다.

하지만, 최근 수년간 새로운 전송 프로토콜을 만들려는 노력은 인터넷에서 그것을 배포하는 어려움 때문에 완전히 멈춰 있다.
새 프로토콜 배포는 그 프로토콜이 도달해야 하는 사용자와 서버 사이에 있는 TCP와 UDP만 허용하는 
방화벽, NAT, 라우터 등의 미들박스에 의해 방해받고 있다. 다른 전송 프로토콜의 도입은 UDP 또는 TCP 가 아닌 경우 
이를 악의적이거나 뭔가 잘못되었다고 판단하고 차단해 버리는 박스들에 의해 차단되므로 연결의 N%가 실패한다. 
노력을 기울이기에 N% 실패율은 너무 높다고 여겨진다.

게다가 보통 네트워크 스택의 전송 프로토콜 계층에서 뭔가를 바꾼다는 것은 보통 운영체제 커널에서 구현한
프로토콜을 말한다. 새로운 운영체제 커널을 갱신하고 배포하는 것은 상당한 노력이 필요한 느린 과정이다.
IETF가 표준화한 수많은 TCP 개선사항도 광범위하게 지원되지 않아서 널리 배포되거나 사용되지 않고 있다.

## 왜 SCTP-over-UDP가 아닌가

SCTP는 스트림을 가진 신뢰성 있는 전송 프로토콜이고 WebRTC처럼 UDP 위에서 이 프로토콜을
사용하는 기존의 구현체도 있다.

다음의 몇 가지 이유로 QUIC의 대체재로 충분하지 않다고 생각했다.

 - SCTP는 스트림에 대해 head-of-line 블로킹 문제를 고치지 못한다
 - SCTP는 연결을 설정할 때 스트림의 수를 결정해야 한다
 - SCTP에는 견고한 TLS/보안에 대한 언급이 없다
 - SCTP는 4단계 핸드쉐이크(4-way handshake)를 사용하고 QUIC은 0-RTT를 제공한다
 - QUIC는 TCP 같은 바이트스트림(bytestream)이고 SCTP는 메시지 기반이다
 - QUIC 연결은 IP 주소 사이에서 마이그레이션을 할 수 있지만 SCTP는 할 수 없다

자세한 차이점이 알고 싶다면
[A Comparison between SCTP and QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00)을
참고하라.
