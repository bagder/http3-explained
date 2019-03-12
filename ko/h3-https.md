<!--
# HTTPS:// URLs

HTTP/3 will be performed using `HTTPS://` URLs. The world is full of these
URLs and it has been deemed impractical and downright unreasonable to
introduce another URL scheme for the new protocol. Much like HTTP/2 did not
need a new scheme, neither will HTTP/3.

The added complexity in the HTTP/3 situation is however that where HTTP/2 was
a completely new way of transporting HTTP over the wire, it was still based on
TLS and TCP like HTTP/1 was. The fact that HTTP/3 is done over QUIC changes
things in a few important aspects.

Legacy, clear-text, `HTTP://` URLs will be left as-is and as we proceed
further into a future with more secure transfers they will probably become
less and less frequently used. Requests to such URLs will simply not be
upgraded to use HTTP/3. In reality they rarely upgrade to HTTP/2 either, but
for other reasons.

## Initial connection

The first connection to a fresh, not previously visited host for a
HTTPS:// URL probably has to be done over TCP (possibly in addition to a
parallel attempt to connect via QUIC). The host might be a legacy server without
QUIC support or there might be a middle box in between setting up obstacles
preventing a QUIC connection from succeeding.

A modern client and server would presumably negotiate HTTP/2 in the first
handshake. When the connection has been setup and the server responds to a
client HTTP request, the server can tell the client about its support of and
preference for HTTP/3.
-->

# HTTPS:// URL

HTTP/3는 `HTTPS://` URL을 사용해서 실행될 것이다. 세상은 이러한 URL로 가득 차 있고
새로운 프로토콜에 또 다른 URL 스킴을 도입하는 것은 실용적이지도 않고 완전히 불합리하다고
여겨졌다. HTTP/2에 새로운 스킴이 필요 없었듯이 HTTP/3에도 필요 없다.

하지만 HTTP/2가 유선으로 HTTP를 전송하는 완전히 새로운 방법이지만 HTTP/1이 그랬듯이 여전히
TLS와 TCP에 기반을 두고 있었기에 HTTP/3 상황에서 복잡성을 추가하게 되었다.
HTTP/3가 QUIC을 통해 수행된다는 점은 몇 가지 중요한 관점에서 변경이 발생했다.

레거시, 평문, `HTTP://` URL은 지금 그대로 유지될 것이지만 더 안전한 전송을 하는 미래로 나아갈수록
점점 덜 사용될 것이다. 이러한 URL에 대한 요청은 HTTP/3를 사용하도록 업그레이드되지 않을 것이다.
현실에서 이러한 것들이 HTTP/2로 업그레이드하는 경우는 거의 없지만 다른 이유 때문이다.

## 초기 연결

이전에 방문한 적이 없는 HTTPS:// URL에 대한 새로운 첫 연결은 아마도 TCP를 통해 수행될 것이다.
(추가로 QUIC을 통한 병렬연결 시도가 있을 수 있다.) 호스트가 QUIC을 지원하지 않는 레거시 서버일
수도 있고 중간에 있는 미들박스가 QUIC 연결이 성공적으로 이뤄지지 않도록 하는 장애물일 수도 있다.

최신 클라이언트와 서버는 아마도 첫 핸드쉐이크에서 HTTP/2를 협상할 것이다. 연결이 설정되고
클라이언트의 HTTP 요청에 서버가 응답할 때 서버는 HTTP/3의 지원과 선호도에 관해
클라이언트에게 알려줄 수 있다.
