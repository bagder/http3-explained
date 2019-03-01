<!--
# QUIC v2

In order to get the most possibly focus on the core QUIC protocol and be able
to ship it on time, several features that were originally planned to be part
of the core protocol have been postponed and are now planned to instead get
done in a subsequent QUIC version. QUIC version 2 or beyond.

The author of this document does however have a rather faulty crystal ball so
we can not tell for sure exactly what features will or will not appear in
version 2. We can however mention some of the features and things that
explicitly have been removed from the v1 work to be "worked on later" and that
then possibly might appear in a version 2.

## Forward Error Correction

Forward error correction (FEC) is a method of obtaining error control in data
transmission in which the transmitter sends redundant data and the receiver
recognizes only the portion of the data that contains no apparent errors.

Google experimented with this in their original QUIC work but it was
subsequently removed again since the experiments did not turn out well. This
feature is subject for discussion for QUIC v2 but probably takes for someone
to prove that it actually can be a useful addition without too much penalty.

## Multipath

Multipath means that the transport can by itself use multiple network paths to
maximize resource usage and increase redundancy.

The SCTP proponents of the world like to mention that SCTP already features
multipath and so does modern TCP.

## Unreliable data

It has been discussed to offer "unreliable" streams as an option, that would
then allow QUIC to also replace UDP-style applications.

## Non-HTTP adaptions

DNS over QUIC was one of the early mentioned non-HTTP protocols that just
might get some attention once QUIC v1 and HTTP/3 ship. But with a new
transport like this having been brought on to the world I cannot imagine that
it will stop there.
-->

# QUIC v2

핵심 QUIC 프로토콜에 가장 집중해서 제때 출시할 수 있도록 핵심 프로토콜의 일부로 원래 계획되어 있던
몇 가지 기능을 연기했고 QUIC 2나 그 뒤 후속 QUIC 버전에 포함할 예정이다.

하지만 이 문서의 작성자가 잘못된 예측을 할 수도 있으므로 버전 2에 어떤 기능이 들어가고 어떤 기능이
안 들어갈지 정확하게 얘기할 수는 없다. 그래도 버전 1에서 명시적으로 제거되어 "나중에 작업"하기로 해서
버전 2에 포함될 가능성이 있는 기능은 얘기할 수 있다.

## 순방향 오류 정정(Forward Error Correction)

순방향 오류 정정(FEC)은 데이터 전송에서 오류 제어를 하는 방법으로 송신기는 중복 데이터를 전송하고
받는 쪽에서는 식별할 수 있는 오류가 없는 데이터의 부분만을 인식한다.

Google이 원래의 QUIC 작업에서 이를 실험했지만, 실험 결과가 좋지 않아서 후에 다시 제거되었다.
이 기능은 QUIC v2의 토론 주제이지만 너무 큰 불이익이 없고 유용한 기능이라는 것을
실제로 누군가 증명해야 할 것이다.

## 다중 경로

다중 경로는 리소스 사용을 최대화하고 중복을 늘리기 위해 전송 자체가 다중 네트워크 경로를
사용하는 것을 의미한다.

SCTP 지지자는 SCTP에는 이미 다중 경로 기능이 있고 오늘날의 TCP도 그렇다고 말할 것이다.

## 신뢰할 수 없는 데이터

"신뢰할 수 없는" 스트림을 선택사항으로 제공해서 UDP 방식의 애플리케이션도
QUIC이 대체할 수 있게 하는 것이 논의되었다.

## HTTP가 아닌 프로토콜 도입

QUIC을 통한 DNS는 QUIC v1과 HTTP/3가 출시되면 관심을 끌 수 있는 HTTP가 아닌 프로토콜로
초기에 언급된 것 중 하나이다. 하지만 이 새로운 전송을 세상에 내놓으면 거기서 끝이라고 상상할 수 없다.
