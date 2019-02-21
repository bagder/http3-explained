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

HTTP 계층은 HTTP 형태의 전송을 한다. 그 중에는 HPACK이라 부르는 HTTP/2 헤더 압축과
비슷한 QPACK을 사용한 HTTP 헤더 압축도 있다.

HPACK 알고리즘은 *순차적인* 스트림 전달에 의존하는데 QUIC은 스트림을 순서 없이
전달할 수 있으므로 HPACK을 수정하지 않고는 HTTP/3에서 재사용할 수 없다. [HPACK](https://httpwg.org/specs/rfc7541.html)을
QUIC에 맞게 수정한 것을 QPACK이라 볼 수 있다.
