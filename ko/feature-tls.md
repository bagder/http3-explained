<!--
## TLS 1.3

The transport security used in QUIC is using TLS 1.3 ([RFC
8446](https://tools.ietf.org/html/rfc8446)) and there are never any unencrypted
QUIC connections.

TLS 1.3 has several advantages compared to older TLS versions but a primary
reason for using it in QUIC is that 1.3 changed the handshake to require fewer
roundtrips. It reduces protocol latency.

The Google legacy version of QUIC used a custom crypto.
-->

## TLS 1.3

QUIC에서 사용하는 전송 보안은 TLS 1.3([RFC 8446](https://tools.ietf.org/html/rfc8446))이며
암호화하지 않은 QUIC 연결은 절대로 존재하지 않는다.

이전 버전의 TLS와 비교해서 TLS 1.3에 몇몇 장점이 있지만 QUIC이 TLS 1.3을 사용한
주된 이유는 핸드쉐이크에 더 적은 라운드 트립이 필요하도록 바뀌었기 때문이다.
이는 프로토콜 지연을 줄여준다.

QUIC의 Google 레거시 버전은 커스텀 암호화를 사용했다.
