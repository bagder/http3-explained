<!--
## Transport and application level

The IETF QUIC protocol is a transport protocol, on top of which other
application protocols can be used. The initial application layer protocol is
HTTP/3 (h3).

The transport layer supports connections and streams.

The legacy Google version of QUIC had transport and HTTP glued together into
one single do-it-all and was a more special-purpose
send-http/2-frames-over-udp protocol.
-->

## 전송 계층과 애플리케이션 계층

IETF QUIC 프로토콜은 전송 프로토콜로써 다른 애플리케이션 프로토콜이 그 위에서 사용할 수 있다.
초기 애플리케이션 계층 프로토콜은 HTTP/3(h3)다.

전송 계층은 연결과 스트림을 지원한다.

레거시 Google 버전 QUIC은 전송과 HTTP가 하나로 합쳐져 있어서
(Quic) 보다 더 특수한 목적의 send-http/2-frames-over-udp 프로토콜이었다.
