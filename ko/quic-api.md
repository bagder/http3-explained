<!--
# API

One of the success factors for regular TCP and programs using that, is the
standardized socket API. It has well defined functionality and using this API
you can move programs between many different operating systems as TCP works
the same.

QUIC is not there. There is no standard API for QUIC.

With QUIC, you need to pick one of the existing library implementations and
stick with its API. It makes applications "locked in" to a single library to
some extent. Changing to another library means another API and that might
involve a lot of work.

Also, since QUIC is typically implemented in user-space, it can't easily just
extend the socket API or appear similar to how existing TCP and UDP
functionality do. Using QUIC will mean using another API than the socket API.
-->

# API

TCP와 TCP를 사용하는 프로그램의 성공 요소 중 하나는 표준화된 소켓 API이다. 소켓 API는
기능이 잘 정의되어 있고 이 API를 사용하면 TCP가 똑같이 동작하므로
다수의 다른 운영체제 사이에서 프로그램을 이동시킬 수 있다.

QUIC은 그렇지 않다. QUIC에는 표준 API가 없다.

QUIC에서는 기존 라이브러리 구현체 중 하나를 선택하고 그 API를 따라야 한다.
이는 애플리케이션을 어떤 부분에서 하나의 라이브러리에 "락인(locked in)"시킨다.
다른 라이브러리로 바꾼다는 것은 다른 API를 뜻하므로 많은 작업이 필요할 것이다.

또한 QUIC이 보통 사용자 영역에서 구현되므로 소켓 API를 쉽게 확장할 수 없고
기존의 TCP나 UDP 기능과 비슷하게 보일 수 없다. QUIC을 사용한다는 것은 소켓 API와는
다른 API를 사용한다는 것을 의미한다.
