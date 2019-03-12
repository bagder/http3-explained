<!--
# Ossification

The internet is a network of networks. There is equipment set up on the
Internet in many different places along the way to make sure this network of
networks works as it is supposed to. These devices, the boxes that are
distributed out in the network, are what we sometimes refer to as middle-boxes.
Boxes that sit somewhere between the two end-points that are the primary parties
involved in a traditional network data transfer.

These boxes serve many different specific purposes but I think we can say that
universally they are put there because someone thinks they must be there to
make things work.

Middle-boxes route IP packets between networks, they block malicious traffic,
they do NAT (Network Address Translation), they improve performance, some try
to spy on the passing traffic and more.

In order to perform their duties these boxes must know about networking and
the protocols that are monitored or modified by them. They run software for
this purpose. Software that is not always upgraded frequently.

While they are glue components that keep the Internet together they are also
often not keeping up with the latest technology. The middle of the network
typically does not move as fast as the edges, as the clients and the servers of
the world.

The network protocols that these boxes might want to inspect, and have ideas
about what is okay and what is not then have this problem: these boxes were
deployed some time ago when the protocols had a feature set of that
time. Introducing new features or changes in behavior that were not known
before risks ending up considered bad or illegal by such boxes. Such traffic
may well just be dropped or delayed to the degree that users really do not
want to use those features.

This is called "protocol ossification".

Changes to TCP also suffer from ossification: some boxes between a client and
the remote server will spot unknown new TCP options and block such connections
since they do not know what the options are. If allowed to detect protocol
details, systems learn how protocols typically behave and over time it becomes
impossible to change them.

The only truly effective way to "combat" ossification is to encrypt as much of
the communication as possible in order to prevent middle-boxes from seeing much
of the protocol passing through.
-->

# 경화(Ossification)

인터넷은 네트워크의 네트워크다. 이 네트워크의 네트워크가 의도대로 동작하게 하는 장비가 인터넷
여러 곳에 설치되어 있다. 우리는 이러한 기기(네트워크에 분포된 박스)를 미들박스라고 부른다.
이 박스는 전통적인 네트워크 데이터 전송의 주요 요소인 두 엔드포인트 사이에 있다.

박스는 여러 가지 다른 목적이 있지만 무언가 동작하게 하려면 이 박스가 해당 위치에 있어야 한다고
누군가 생각했기 때문에 곳곳에 깔린 것이라 생각한다.

미들박스는 네트워크 사이에서 IP 패킷을 라우팅하고, 악성 트래픽을 차단하고,
NAT(Network Address Translation) 역할을 하고, 성능을 향상시키고, 통과하는
트래픽을 감시하는 등의 역할을 한다.

이러한 박스는 의무를 다하려면 자신들이 모니터링하고 수정하는 네트워크 및 프로토콜에 대해
반드시 알아야 한다. 박스는 이런 목적으로 소프트웨어를 실행한다. 그 소프트웨어를
항상 자주 업그레이드하는 것은 아니다.

박스는 인터넷이 유지되도록 연결하는 구성 요소이지만 종종 최신 기술을 따라잡지 못하는 경우가 있다.
보통 네트워크 중간 영역은 전 세계의 클라이언트나 서버 같은 엣지 만큼 빠르게 바뀌지 않는다.

어떤 프로토콜을 검사하기를 원하는지, 그리고 어떤것이 괜찮고 안 괜찮은지 알고있는 박스들은
과거에 배포되었고 그 당시의 프로토콜 기능 셋을 가지고 있다.
이전에는 몰랐던 새로운 기능이나 동작의 변경 사항이 추가되면 박스가 이를 잘못된 것이나 허용하지
않는 것으로 판단할 위험이 있다. 그래서 이러한 트래픽은 사용자가 해당 기능을 사용하고
싶지 않을 정도로 지연되거나 중단될 수 있다.

이를 "프로토콜 경화(ossification)"라고 부른다.

TCP를 변경하는 것도 경화 문제를 겪는다. 클라이언트와 원격 서버 사이에 있는 박스 중 일부는
알지 못하는 새로운 TCP 옵션을 발견하고 이 옵션이 무엇인지 몰라서 해당 연결을 차단해버릴 것이다.
프로토콜의 상세 내용을 탐지하도록 허용한 경우 시스템은 프로토콜이 보통 어떻게 동작하는지
배우게 되고 시간이 지나면 프로토콜을 변경할 수 없게 된다.

유일하게 경화를 "방지하는데" 효과적인 방법은 미들박스가 지나가는 프로토콜에서 많은 것을
볼 수 없도록 통신을 최대한 암호화하는 것이다.
