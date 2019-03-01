<!--
## User-space

Implementing a transport protocol in user-space helps enable quick
iteration of the protocol, as it is comparatively easy to evolve the
protocol without necessitating that clients and servers update their
operating system kernel to deploy new versions.

Nothing inherent in QUIC prevents it from being implemented and offered
by operating system kernels in the future, should someone find that a
good idea.

### Many implementations

One obvious effect of implementing a new transport protocol in
user-space is that we can expect to see many independent implementations.

Different applications are likely to include (or layer atop) different
HTTP/3 and QUIC implementations for the foreseeable future.
-->

## 사용자 영역

사용자 영역에서 전송 프로토콜을 구현하면 클라이언트와 서버가 새로운 버전을 배포하기 위해 운영체제 커널을
업데이트할 필요가 없어서 비교적 쉽게 프로토콜을 발전시킬 수 있으므로 프로토콜을 빠르게 반복할 수 있다.

미래에 운영체제 커널에서 구현되거나 제공하지 않도록 막는 것은 QUIC에 아무것도 없으므로
누군가 좋은 방법을 찾아야 한다.

### 많은 구현체

사용자 영역에서 새로운 전송 프로토콜을 구현하는 한 가지 명백한 효과는
다수의 독립적인 구현체를 볼 수 있다는 것이다.

예견할 수 있는 미래에 다른 애플리케이션은
다른 HTTP/3와 QUIC 구현체를 포함할(또는 계층 위에서) 것이다.
