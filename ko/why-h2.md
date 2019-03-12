<!--
## Remember HTTP/2?

The HTTP/2 specification [RFC 7540](https://httpwg.org/specs/rfc7540.html) was
published in May 2015 and the protocol has since then been implemented and
deployed widely across the Internet and the World Wide Web.

In early 2018, almost 40% of the top-1000 web sites run HTTP/2, around 70% of
all HTTPS requests Firefox issues get HTTP/2 responses back and all major
browsers, servers and proxies support it.

HTTP/2 addresses a whole slew of shortcomings in HTTP/1 and with the
introduction of the second version of HTTP users can stop using a bunch of
work-arounds. Some of which are pretty burdensome on web developers.

One of the primary features of HTTP/2 is that it makes use of multiplexing, so
that many logical streams are sent over the same physical TCP connection. This
makes a lot of things better and faster. It makes congestion control work much
better, it lets users use TCP much better and thus properly saturate the
bandwidth, makes the TCP connections more long-lived - which is good so that
they get up to full speed more frequently than before. Header compression
makes it use less bandwidth.

With HTTP/2, browsers typically use *one* TCP connection to each host instead
of the previous *six*. In fact, connection coalescing and "desharding"
techniques used with HTTP/2 may actually even reduce the number of connections
much more than so.

HTTP/2 fixed the HTTP head of line blocking problem, where clients had to wait
for the first request in line to finish before the next one could go out.

![http2 man](../images/h2-man.jpg)
-->

## HTTP/2를 기억하는가?

HTTP/2 명세인 [RFC 7540](https://httpwg.org/specs/rfc7540.html)는
2015년 5월에 발행되었고 이후 인터넷과 월드 와이드 웹에 널리 구현되고 배포되었다.

2018년 초 상위 1,000개의 웹사이트 중 거의 40%가 HTTP/2로 동작하고 있으며 Firefox가 보낸
모든 HTTPS 요청의 70% 정도가 HTTP/2 응답을 받았고
주요 모든 브라우저와 서버, 프락시가 이를 지원하고 있다.

HTTP/2는 HTTP/1의 수많은 결점을 수정했고 HTTP의 두 번째 버전을 도입함으로써
사용자들이 수많은 우회법을 사용하지 않게 되었다. 그 중 일부는 웹 개발자에게 상당한 부담이었다.

HTTP/2의 주요 기능 중 하나인 멀티플렉싱을 사용하여 같은 물리 TCP 연결을 통해
다수의 논리 스트림을 보낼 수 있게 된 것이다. 이는 많은 것을 더 좋고 빠르게 만들었다.
또한, 혼잡 제어 작업을 훨씬 낫게 해주어 사용자가 TCP를 훨씬 잘 사용하게 되면서 대역폭을
적절하게 가득 채워서 사용해 TCP 연결을 더 오래 유지되도록 만들었다. 이는 이전보다
더 자주 최대 속도를 낼 수 있기 때문에 좋아진 것이다. 헤더 압축은 대역폭을 적게 사용하게끔 해준다.

이전에는 브라우저가 호스트당 *6개의* TCP 연결을 사용했지만, HTTP/2를 사용하면 보통 *하나의* TCP 연결을
사용한다. 사실 HTTP/2에서 연결 병합과 "desharding" 기술을 사용하면
연결 수를 훨씬 더 줄일 수도 있다.

HTTP/2는 클라이언트가 다음 요청을 보내기 전에 첫 요청이 끝나기를 기다려야 하는
HTTP HOL(head of line) 블로킹 문제를 고쳤다.

![http2 man](../images/h2-man.jpg)
