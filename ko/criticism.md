<!--
# Criticism

## UDP will never work

A lot of enterprises, operators and organizations block or rate-limit UDP
traffic outside of port 53 (used for DNS) since it has in recent days mostly
been abused for attacks. In particular, some of the existing UDP protocols and
popular server implementations for them have been vulnerable for amplification
attacks where one attacker can make a huge amount of outgoing traffic to
target innocent victims.

QUIC has built-in mitigation against amplification attacks by requiring that the
initial packet must be at least 1200 bytes and by restriction in the protocol
that says that a server MUST NOT send more than three times the size of the
request in response without receiving a packet from the client in response.

## UDP is slow in kernels

This seems to be the truth, at least today in 2018. We can of course not tell
how this will develop and how much of this is simply the result of UDP
transfer performance not having been in developers' focus for many years.

For most clients, this "slowness" is probably never even noticeable.

## QUIC takes too much CPU

Similar to the "UDP is slow" remark above, this is partly because the TCP and
TLS usage of the world has had a longer time to mature, improve and get
hardware assistance.

There are reasons to expect this to improve over time. The question is how much
this extra CPU usage will hurt deployers.

## This is just Google

No it is not. Google brought the initial spec to the IETF after having proved,
on a large Internet-wide scale, that deploying this style of protocol over UDP
actually works and performs well.

Since then, individuals from a large number of companies and organizations
have worked in the vendor-neutral organization IETF to put together a standard
transport protocol out of it. In that work, Google employees have of course
been participating, but so have employees from a large number of other
companies that are interested in furthering the state of transport protocols
on the Internet, including Mozilla, Fastly, Cloudflare, Akamai, Microsoft,
Facebook and Apple.

## This is too small of an improvement

That is not really a critique but an opinion. Maybe it is, and maybe it is too
little of an improvement so close in time since HTTP/2 was shipped.

HTTP/3 is likely to perform much better in packet loss-ridden networks, it
offers faster handshakes so it will improve latency both as perceived and
actual. But is that enough of benefits to motivate people to deploy HTTP/3
support on their servers and for their services? Time and future performance
measurements will surely tell!
-->

# 일반적인 비판

## UDP는 절대 동작하지 않을 것이다

(DNS에서 사용하는) 53 포트가 아닌 UDP 트래픽이 최근에는 주로 공격에 사용되기 때문에
많은 기업, 운영자, 조직에서 차단하거나 속도를 제한하고 있다. 특히 기존의 UDP 프로토콜과
잘 알려진 서버 구현체 중 일부는 증폭 공격에 대한 취약점이 있으므로 공격자가 무고한 대상 피해자에게
대량의 트래픽을 보낼 수 있다.

QUIC에서는 초기 패킷이 최소 1200바이트여야 한다는 조건과 서버가 클라이언트로부터 응답 패킷을
받지 않으면 요청 크기의 3배 이상은 절대 보내면 안 된다는 프로토콜의 제약사항으로 증폭 공격을
완화하는 기능이 들어있다.

## 커널에서 UDP는 느리다

이는 적어도 2018년 현재까지 사실로 보인다. 물론 앞으로 어떻게 발전할 것인지, 수년간
UDP의 전송 성능이 개발자의 관심사가 아니었다는 결과가 간단히 어느 정도인지 말할 수 없다.

대부분 클라이언트는 이 "느림"을 결코 알아채지 못했다.

## QUIC은 CPU를 너무 많이 사용한다

위에서 얘기한 "UDP는 느리다"와 비슷하게 이 또한 부분적으로는 TCP와 TLS가 세계적으로 더 오랫동안
성숙하고 개선되고 하드웨어의 지원을 받았기 때문이다.

시간이 지나면 개선되리라 기대할 근거는 있다. 문제는 추가적인 CPU 사용이 배포자에게
얼마나 영향을 끼치는가이다.

## 그냥 구글이다

전혀 그렇지 않다. Google이 대규모 인터넷 환경에서 증명을 마친 후 IETF에 초기 명세를 가져왔다.
UDP를 통한 이 방식의 프로토콜 배포는 실제로 잘 동작한다.

그 이후 많은 회사와 조직의 사람들이 벤더 중립적 조직인 IETF에서 독립적으로 표준 전송 프로토콜을
작업했다. 물론 이 작업에 Google 직원도 참여했지만, 인터넷 전송 프로토콜의 상태를 향상하려는
Mozilla, Fastly, Cloudflare, Akamai, Microsoft, Facebook, Apple 등 많은 회사의
직원들도 참여했다.

## 개선된 부분이 너무 적다

이것은 정말 비판이 아니라 의견일 뿐이다. 어쩌면 HTTP/2가 나온 지 얼마 안 되었기 때문에 개선된 부분이
너무 적을 수도 있다.

HTTP/3는 패킷 손실이 많은 네트워크에서 훨씬 더 잘 동작할 것이고, 더 빠른 핸드쉐이크를 제공하므로
체감 지연시간과 실제 지연시간을 모두 개선할 것이다. 하지만, 사람들이 자신의 서버와 서비스에
HTTP/3 지원을 추가하고 싶을 정도로 장점이 충분할까?
시간과 미래의 성능 측정으로 분명히 알 수 있을 것이다!
