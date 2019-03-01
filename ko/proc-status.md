<!--
# Status

The QUIC working group has worked fiercely since late 2016 on specifying the
protocols and the plan is now to have it done by July 2019.

As of November 2018, there still has not been any larger interoperability
tests with HTTP/3 - only with the existing two implementations and none of
them are done by a browser or a popular open server software.

There are fifteen or so different [QUIC implementations
listed](https://github.com/curl/curl/wiki/QUIC-implementation) in the QUIC
working groups' wiki pages, but far from all of them can interoperate on the
latest spec draft revisions.

Implementing QUIC is not easy and the protocol has kept moving and changing
even up to this date.

## Servers

There have been no public statement in terms of support for QUIC from Apache
or nginx.

## Clients

None of the larger browser vendors have yet shipped any version, at any state,
that can run the IETF version of QUIC or HTTP/3.

Google Chrome has shipped with a working implementation of Google's own QUIC
version since many years, but that does not interoperate with the IETF
QUIC protocol and its HTTP implementation is different than HTTP/3.

## Implementation Obstacles

QUIC decided to use TLS 1.3 as the foundation for the crypto and security
layer to avoid inventing something new and instead lean on a trustworthy and
existing protocol. However, while doing this, the working group also decided
that to really streamline the use of TLS in QUIC, it should only use "TLS
messages" and not "TLS records" for the protocol.

This might sound like an innocuous change, but this has actually caused a
significant hurdle for many QUIC stack implementors. Existing TLS libraries
that support TLS 1.3 simply do not have APIs enough to expose this
functionality and allow QUIC to access it. While several QUIC implementors
come from larger organizations who work on their own TLS stack in parallel,
this is not true for everyone.

The dominant open source heavyweight OpenSSL for example, does not have any
API for this and has not expressed any desire to provide any such anytime soon
(as of November 2018).

This will eventually also lead to deployment obstacles since QUIC stacks will
need to either base themselves on other TLS libraries, use a separate patched
OpenSSL build or require an update to a future OpenSSL version.

## Kernels and CPU load

Both Google and Facebook have mentioned that their wide scale deployments of
QUIC require roughly twice the amount of CPU than the same traffic load does
when serving HTTP/2 over TLS.

Some explanations for this include

- the UDP parts in primarily Linux is not at all as optimized as the TCP stack
  is, since it has not traditionally been used for high speed transfers like
  this.

- TCP and TLS offloading to hardware exist, but that is much rarer for UDP and
  basically non-existing for QUIC.

There are reasons to believe that performance and CPU requirements will
improve over time.
-->

# 상태

QUIC 워킹 그룹은 2016년 후반부터 프로토콜을 제정하는 일에 열심히 노력했고 현재 계획은 2019년 7월에 완료하는 것이다.

2018년 11월까지도 HTTP/3의 아직 대규모 연동 테스트를 진행하지 않았다. 기존에 두 개의 구현체가 있는데 둘 다 브라우저나 인기있는 공개 서버 소프트웨어와의 테스트를 하지 않았다.

QUIC 워킹 그룹의 위키 페이지에 나열된 15개 정도의 서로 다른 [QUIC 구현체](https://github.com/curl/curl/wiki/QUIC-implementation)가 있지만 이들 모두 최신 명세 드래프트 개정판과 연동되지 않는다.

QUIC을 구현하는 것은 쉽지 않고 프로토콜은 오늘날 까지도 계속 진화하며 변하고 있다.

## 서버

지금까지 Apache나 nginx에서 공개적으로 QUIC을 지원한다는 발표는 없다.

## 클라이언트

아직 대형 브라우저 벤더중 아무도 QUIC이나 HTTP/3의 IETF 버전을 실행할 수 있는 버전을 제공하거나 발표하지 않았다.

수년간 Google Chrome은 Google 자체의 QUIC 버전의 구현체를 포함해서 배포했지만 이는 IETF QUIC 프로토콜과 연동되지 않고 그 HTTP 구현체는 HTTP/3와도 다르다.

## 구현 방해물

QUIC은 뭔가 새로운 것을 발명하지 않고 신뢰할 수 있는 기존 프로토콜을 사용하고자 TLS 1.3을 암호화와
보안 계층의 기반으로 사용하기로 했다. 하지만 이 작업을 하면서 워킹 그룹은 QUIC에서 TLS의 사용을
실제로 간소화하기로 발표했다. 즉, 프로토콜은 "TLS 레코드"는 사용하지 않고
"TLS 메시지"만 사용해야 한다.

이것이 무해한 변화처럼 들릴 수 있지만 수많은 QUIC 스택 구현자들에게는 커다란 걸림돌이 되었다.
TLS 1.3을 지원하는 기존 TLS 라이브러리는 이 기능을 공개하거나 QUIC이 접근할 수 있는 API가 충분치 않다.
더 큰 조직에서 온 몇몇 QUIC 구현자들은 자신들의 TLS 스택에도 동시에 작업을 하고 있지만 모두가 그런 것은 아니다.

예시로 중량급 지배적 오픈 소스인 OpenSSL은 이에 대한 API가 전혀 없고 근래에 제공할 의사를
밝힌 적이 없다.(2018년 11월 기준)

이는 QUIC 스택이 다른 TLS 라이브러리(별도로 수정한 OpenSSL 빌드)를 사용하거나 향후 OpenSSL 버전을 수정할
필요가 있기 때문에 결국 배포 상의 걸림돌이다.

## 커널과 CPU 부하

Google과 Facebook은 QUIC의 대규모 배포가 TLS에서 HTTP/2로 서비스 할때보다
같은 트래픽 기준으로 거의 2배의 CPU가 필요하다고 얘기했다.

이는 다음과 같은 이유 때문이다.

- 본질적으로 Linux의 UDP 부분은 TCP 스택만큼 최적화되어 있지 않다. 이는 전통적으로 지금처럼
  고속 전송에 사용해오지 않았기 때문이다.

- 하드웨어가 TCP와 TLS의 부담을 덜어주고 있지만 UDP에 대해서 그렇게 하는 경우는 드물고
  기본적으로 QUIC에 대해서는 아예 존재하지 않는다.

시간이 지나면 성능 및 필요한 CPU가 개선될 것이라고 생각한다.
