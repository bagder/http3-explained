<!--
# Alt-svc

The alternate service (Alt-svc:) header and its corresponding `ALT-SVC` HTTP/2
frame are not specifically created for QUIC or HTTP/3. They are part of an
already designed and created mechanism for a server to tell a client: *"look,
I run the same service on THIS HOST using THIS PROTOCOL on THIS PORT"*. See
details in [RFC 7838](https://tools.ietf.org/html/rfc7838).

A client that receives such an Alt-svc response is then advised to, if it
supports and wants to, connect to that given other host in parallel in the
background - using the specified protocol - and if it is successful switch its
operations over to that instead of the initial connection.

If the initial connection uses HTTP/2 or even HTTP/1, the server can respond
and tell the client that it can connect back and try HTTP/3. It could be to
the same host or to another one that knows how to serve that origin. The
information given in such an Alt-svc response has an expiry timer, making
clients able to direct subsequent connections and requests directly to the
alternative host using the suggested alternative protocol, for a certain
period of time.

## Example

An HTTP server includes an `Alt-Svc:` header in its response:

    Alt-Svc: h3=":50781"

This indicates that HTTP/3 is available on UDP port 50781 at the same host name
that was used to get this response.

A client can then attempt to setup a QUIC connection to that destination and
if successful, continue communicating with the origin like that instead of the
initial HTTP version.
-->

# Alt-svc

대체 서비스 헤더(Alt-svc:)와 이에 대응되는 `ALT-SVC` HTTP/2 프레임이 QUIC이나
HTTP/3를 위해 특별히 만들어진 것은 아니다. 서버가 클라이언트에게
*"봐라. 이 포트에서 이 프로토콜로 이 호스트에서 같은 서비스를 운영하고 있다."*라고 말할 수 있도록
이미 설계되고 만들어진 메커니즘의 일부이다.
자세한 내용은 [RFC 7838](https://tools.ietf.org/html/rfc7838)를 참고해라.

이러한 Alt-svc 응답을 받은 클라이언트는 (이를 지원하고 원하는 경우) 주어진 다른 호스트에 지정된
프로토콜로 백그라운드에서 병렬 연결을 하도록 권고받는다. 성공적으로 전환된다면 초기 연결 대신
새로운 연결을 통해서 해당 작업을 수행한다.

초기 연결이 HTTP/2나 HTTP/1을 사용하더라도 서버는 다시 연결해서 HTTP/3를 시도할 수 있다고
클라이언트에게 알려줄 수 있다. 이는 같은 호스트일 수도 있고 요청한 내용을 제공하는 방법을 아는
다른 호스트일 수도 있다. 이러한 Alt-svc 응답에서 제공된 정보에는 만료 타이머가 있어서,
클라이언트가 일정 시간 동안 제안받은 대체 프로토콜로 직접 대체 호스트에 이어진 연결과 요청을 할 수 있다.

## 예시

HTTP 서버는 응답에 `Alt-Svc:` 헤더를 다음과 같이 포함한다.

    Alt-Svc: h3=":50781"

이는 해당 응답을 얻는데 사용한 것과 같은 호스트 이름의 50781 UDP 포트에서
HTTP/3를 사용할 수 있음을 나타낸다.

그 다음 클라이언트는 해당 목적지에 QUIC 연결을 설정하려고 시도하고 연결이 성공하면
초기 HTTP 버전 대신 이러한 출처와 계속해서 통신한다.
