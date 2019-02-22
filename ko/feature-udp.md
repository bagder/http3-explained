<!--
## Transfer protocol over UDP

QUIC is a transfer protocol implemented on top of UDP. If you watch your network
traffic casually, you will see QUIC appear as UDP packets.

Based on UDP it also then uses UDP port numbers to identify specific network
services on a given IP address.

All known QUIC implementations are currently in user-space, which allows for
more rapid evolution than kernel-space implementations typically allow.

## Will it work?

There are enterprises and other network setups that block UDP traffic on other
ports than 53 (used for DNS). Others throttle such data in ways that makes
QUIC perform worse than TCP based protocols. There is no end to what some
operators may do.

For the foreseeable future, all use of QUIC-based transports will probably
have to be able to gracefully fall-back to another (TCP-based) alternative.
Google engineers have previously mentioned measured failure rates in the low
single-digit percentages.

## Will it improve?

Chances are that if QUIC proves to be a valuable addition to the Internet
world, people will want to use it and they will want it to function in their
networks and then companies may start to reconsider their obstacles. During
the years the development of QUIC has progressed, the success rate for
establishing and using QUIC connections across the Internet has increased.
-->

## UDP 상의 전송 프로토콜

QUIC은 UDP 위에 구현한 전송 프로토콜이다. 우리가 임의로 네트워크 트래픽을 보면
QUIC이 UDP 패킷으로 나타나는 것을 볼 것이다.

UDP에 기반을 둔 QUIC은 UDP 포트 번호를 사용해서 주어진 IP 주소의 특정 네트워크 서비스를 식별한다.

현재 알려진 모든 QUIC 구현체는 사용자 영역에 있으므로 커널 영역의 구현체보다 훨씬 빠른 발전이 가능하다.

## 동작할 것인가?

(DNS에 사용되는) 53 포트가 아닌 포트의 UDP 트래픽을 차단하는 기업용 및 기타 네트워크 설정이 있다.
또 다른 설정은 여러 방법으로 이러한 데이터를 제한하기 때문에 QUIC은 TCP에 기반을 둔 프로토콜보다
성능이 더 좋지 않다. 이 때문에, 몇몇 운영자가 해야 할 일에는 끝이 없다.

가까운 미래에 QUIC 기반의 모든 전송은 아마도 그레이스풀하게 (TCP 기반의) 다른 대안 프로토콜로
전환될 수 있어야 한다. Google 엔지니어는 측정한 실패 비율이 낮은 한 자릿수라고 얘기했다.

## 나아질 것인가?

QUIC이 인터넷 세상에 가치를 더할 수 있다고 증명한다면 사람들은 사용하기를 원할 것이고 그들의
네트워크에서 동작하길 원할 것이다. 그러면 회사들은 자신들의 장애물을 재고하기 시작할 것이다.
수년간 QUIC 개발은 진척이 있었으며, 인터넷에서 QUIC 연결을 설정하고 사용하는 성공률이 증가하고 있다.
