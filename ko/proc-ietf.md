<!--
## IETF

The QUIC working group that was established to standardize the protocol within
the IETF quickly decided that the QUIC protocol should be able to transfer
other protocols than "just" HTTP. Google-QUIC only ever transported HTTP -
in practice it transported what was effectively HTTP/2 frames, using the
HTTP/2 frame syntax.

It was also stated that IETF-QUIC should base its encryption and security on
TLS 1.3 instead of the "custom" approach used by Google-QUIC.

In order to satisfy the send-more-than-HTTP demand, the IETF QUIC protocol
architecture was split in two separate layers: the transport QUIC and the
"HTTP over QUIC" layer (the latter sometimes referred to as "hq").

This layer split, while it may sound innocuous, has caused the IETF-QUIC to
differ quite a lot from the original Google-QUIC.

The working group did however soon decide that in order to get the proper focus
and ability to deliver QUIC version 1 on time, it would focus on delivering
HTTP, leaving non-HTTP transports to later work.

In March 2018 when we started working on this book, the plan was to ship the
final specification for QUIC version 1 in November 2018; this was later
postponed to July 2019.

While the work on IETF-QUIC has progressed, the Google team has incorporated
details from the IETF version and has started to slowly progress their version
of the protocol towards what the IETF version might become. Google has continued
using their version of QUIC in their browser and services.

[Most new implementations under development](https://github.com/quicwg/base-drafts/wiki/Implementations)
have decided to focus on the IETF version and are not compatible with the Google version.
-->

## IETF

IETF에서 프로토콜을 표준화하려고 만든 QUIC 워킹 그룹은 QUIC 프로토콜이 "단순히" HTTP가 아닌 다른 
프로토콜을 전송할 수 있어야 한다고 빠르게 결정했다. Google-QUIC은 오로지 HTTP만 전송했고
실제로 HTTP/2 프레임 문법을 사용해서 HTTP/2 프레임을 효과적으로 전송했다.

IETF-QUIC은 Google-QUIC이 사용한 "커스텀" 접근 방법이 아니라 TLS 1.3의 암호화와 보안을
기반으로 두어야 한다고도 발표했다.

HTTP보다 더 많이 보내야 한다는 요구를 만족시키기 위해 IETF QUIC 프로토콜 아키텍처를 두 가지
별도의 계층인 전송 QUIC과 "HTTP over QUIC" 계층(후자는 종종 "hq"라고도 한다)으로 분할했다.

무해할 것처럼 들렸던 이 계층 분할로 인해 IETF-QUIC은 원래의 Google-QUIC과 많이 달라졌다.

하지만 워킹 그룹은 곧 적절하게 집중해서 제때 QUIC 버전 1을 제공할 수 있도록 HTTP를 제공하는 데
집중하고 HTTP가 아닌 전송은 나중 작업으로 남겨두기로 했다.

2018년 3월 이 책의 작업을 시작할 때 QUIC 버전 1의 최종 명세를 2018년 11월에 발표 할 계획이었다.
이는 나중에 2019년 7월로 연기되었다.

IETF-QUIC 작업이 진행되는 동안 Google 팀은 IETF 버전의 세부 내용을 받아들였고
IETF 버전이 만들어질 방향으로 Google 버전의 프로토콜을 천천히 발전시켰다.
Google은 자사의 브라우저와 서비스에서 QUIC의 Google 버전을 계속해서 사용하고 있다.

[개발 중인 대부분의 새로운 구현](https://github.com/quicwg/base-drafts/wiki/Implementations)은
IETF 버전에 집중하고 Google 버전과는 호환되지 않는다.
