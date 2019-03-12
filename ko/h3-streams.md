<!--
# QUIC streams and HTTP/3

HTTP/3 is made for QUIC so it takes full advantage of QUIC's streams, where
HTTP/2 had to design its entire stream and multiplexing concept of its own on
top of TCP.

HTTP requests done over HTTP/3 use a specific set of streams.

## HTTP/3 frames

HTTP/3 means setting up QUIC streams and sending over a set of frames to the
other end. There's but a small fixed number (actually nine on December 18th, 2018!) of known frames in
HTTP/3. The most important ones are probably:

- HEADERS, that sends compressed HTTP headers
- DATA, sends binary data contents
- GOAWAY, please shutdown this connection

## HTTP Request

The client sends its HTTP request on a client-initiated *bidirectional* QUIC
stream.

A request consists of a single HEADERS frame and might optionally be followed
by one or two other frames: a series of DATA frames and possibly a final
HEADERS frame for trailers.

After sending a request, a client closes the stream for sending.

## HTTP Response

The server sends back its HTTP response on the bidirectional stream. A HEADERS
frame, a series of DATA frames and possibly a trailing HEADERS frame.

## QPACK headers

The HEADERS frames contain HTTP headers compressed using the QPACK algorithm.
QPACK is similar in style to the HTTP/2 compression called HPACK ([RFC
7541](https://httpwg.org/specs/rfc7541.html)), but modified to work with
streams delivered out of order.

QPACK itself uses two additional unidirectional QUIC streams between the two
end-points. They are used to carry dynamic table information in either
direction.
-->

# QUIC 스트림과 HTTP/3

HTTP/3가 QUIC을 위해 만들어졌으므로 HTTP/2는 전체 스트림과 TCP 위에서 자체 멀티플랙싱 개념을
설계해야 하는 QUIC 스트림의 이점을 최대한 활용한다.

HTTP/3를 통해 수행되는 HTTP 요청은 특정 스트림 세트를 사용한다.

## HTTP/3 프레임

HTTP/3는 QUIC 스트림을 설정하고 반대쪽 끝으로 프레임 세트를 보내는 것을 의미한다.
HTTP/3에는 몇 가지 알려진 프레임이 고정되어 있다. 이 중 가장 중요한 것은 다음과 같다.

- HEADERS, 압축된 HTTP 헤더를 보내라.
- DATA, 바이너리 데이터 콘텐츠를 보내라.
- GOAWAY, 이 연결을 종료해라.

## HTTP 요청

클라이언트는 클라이언트가 초기화한 *양방향* QUIC 스트림으로 HTTP 요청을 보낸다.

단일 HEADERS 프레임으로 구성된 요청은 하나 또는 두 개의 다른 프레임, 즉 일련의 DATA 프레임과
뒤이어 오는 것들을 위한 최종 HEADERS 프레임이 따라올 수 있다.

요청을 보낸 후 클라이언트는 전송용 스트림을 닫는다.

## HTTP 응답

서버는 양방향 스트림으로 해당 HTTP 응답을 돌려보낸다. 여기에는 HEADERS 프레임과 일련의 DATA 프레임이 있고
뒤따라오는 HEADERS 프레임이 있을 수 있다.

## QPACK 헤더

HEADERS 프레임은 QPACK 알고리즘으로 압축된 HTTP 헤더를 담고 있다. QPACK은 HPACK이라고 부르는
HTTP/2의 압축과 형식 면에서 비슷하지만, 순서가 맞지 않게 전송된 스트림에서 동작하도록 수정되었다.

QPACK 자체는 두 엔드포인트 사이에서 추가적인 두 개의 단방향 QUIC 스트림을 사용한다.
이 스트림은 양방향으로 동적 테이블 정보를 전달하는 데 사용된다.
