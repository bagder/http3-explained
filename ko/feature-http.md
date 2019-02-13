<!--
## HTTP/3

The HTTP layer does HTTP-style transports, including HTTP header compression
using QPACK - which is similar to the HTTP/2 compression named HPACK.

The HPACK algorithm depends on an *ordered* delivery of streams so it was not
possible to reuse it for HTTP/3 without modifications since QUIC offers
streams that can be delivered out of order. QPACK can be seen as the
QUIC-adapted version of [HPACK](https://httpwg.org/specs/rfc7541.html).
-->

## HTTP/3

HTTP 계층은 QPACK으로 HTTP 헤더 압축을 포함해서 HTTP 형식의 전송을 수행한다.
이는 HPACK이라 부르는 HTTP/2 헤더 압축과 비슷하다.

HPACK 알고리즘은 *순서가 유지된* 스트림의 전달에 의존하는데 QUIC의 스트림은 순서가 바뀌어서
전달될 수 있으므로 수정하지 않고는 HTTP/3에서 HPACK을 재사용할 수 없다. QPACK을 QUIC에 맞게
수정된 [HPACK](https://httpwg.org/specs/rfc7541.html)이라고 볼 수 있다.
