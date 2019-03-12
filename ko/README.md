<!--
# HTTP/3 explained

This book effort was started in March 2018. The plan is to document HTTP/3 and
its underlying protocol: QUIC. Why, how they work, protocol details, the
implementations and more.

The book is entirely free and is meant to be a collaborative effort
involving anyone and everyone who wants to help out.

## Prerequisites

A reader of this book is presumed to have a basic understanding of TCP/IP
networking, the fundamentals of HTTP and the web. For further insights and
specifics about HTTP/2 we recommend first reading up the details in [http2
explained](https://daniel.haxx.se/http2/).

## Author

This book is created and the work is started by [Daniel
Stenberg](https://daniel.haxx.se/). Daniel is the founder and lead developer
of [curl](https://curl.haxx.se/), the world's most widely used HTTP client
software. Daniel has worked with and on HTTP and internet protocols for over
two decades and is the author of [http2
explained](https://daniel.haxx.se/http2/).

## Home

The home page for this book is found at
[daniel.haxx.se/http3-explained](https://daniel.haxx.se/http3-explained).

## Help out

If you find mistakes, omissions, errors or blatant lies in this document,
please send us a refreshed version of the affected paragraph and we will make
amended versions. We will give proper credits to everyone who helps out. I
hope to make this document better over time.

Preferably, you submit [errors](https://github.com/bagder/http3-explained/issues)
or [pull requests](https://github.com/bagder/http3-explained/pulls) on the book's
github page.

## License

This document and all its contents are licensed under the [Creative Commons
Attribution 4.0 license](https://creativecommons.org/licenses/by/4.0/).
-->

# HTTP/3 해설

이 책은 2018년 3월에 작성하기 시작했다. HTTP/3와 그 기반 프로토콜인 QUIC이 왜, 어떻게 동작하는지와
프로토콜의 상세내용, 그 구현체 등을 설명할 계획이다.

이 책은 완전히 무료이므로 돕고자 하는 사람은 누구나 참여해서 같이 만들 수 있다.

## 사전 요구사항

이 책의 독자는 TCP/IP 네트워크, HTTP의 기본, 웹을 어느 정도 이해하고 있다고 가정한다.
HTTP/2에 대해서 더 알고 싶다면 [http2 explained](https://daniel.haxx.se/http2/)를
읽어보기를 권장한다.

## 저자

이 책은 [Daniel Stenberg](https://daniel.haxx.se/)가 시작해서 만들어졌다. Daniel은
세계에서 가장 널리 사용되는 HTTP 클라이언트 소프트웨어인 [curl](https://curl.haxx.se/)을
만든 사람이자 curl의 리드 개발자다. Daniel은 20년 넘게 HTTP와 인터넷 프로토콜로 일했고
[http2 explained](https://daniel.haxx.se/http2/)의 저자이기도 하다.

## 홈페이지

이 책의 홈페이지는
[daniel.haxx.se/http3-explained](https://daniel.haxx.se/http3-explained)다.

## 도움 요청

이 문서에서 실수, 누락, 오류, 속 보이는 거짓말 등을 발견한다면 해당 문단의 수정 버전과 함께 보내주면
수정하고 도움 준 사람에게 적절한 크레딧을 줄 예정이다. 이 문서가 점점 나아지기를 기대한다.

가능하면 이 책의 github 페이지에
[이슈를 생성](https://github.com/bagder/http3-explained/issues)하거나
[풀 리퀘스트](https://github.com/bagder/http3-explained/pulls)를 제출해주기 바란다.

## 라이센스

이 문서와 모든 내용은 [Creative Commons 저작자표시 4.0
국제 라이센스](https://creativecommons.org/licenses/by/4.0/deed.ko)하에 배포된다.
