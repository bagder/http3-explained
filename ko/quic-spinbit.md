<!--
# Spin Bit

One of the perhaps longest design discussions within the QUIC working group
that has been the subject of several hundred mails and hours of discussions
concerns a single bit: the Spin Bit.

The proponents of this bit insist that there is a need for operators and
people on the path between two QUIC endpoints to be able to measure latency.

The opponents to this feature do not like the potential information leak.

## Spinning a bit

Both endpoints, the client and the server, maintain a spin value, 0 or 1, for
each QUIC connection, and they set the spin bit on packets it sends for that
connection to the appropriate value.

Both sides then send out packets with that spin bit set to the same value
for as long as one round trip lasts and then it toggles the value. The effect
is then a pulse of ones and zeroes in that bitfield that observers can
monitor.

This measuring only works when the sender is neither application nor flow
control limited and packet reordering over the network can also make the data
noisy.
-->

# 스핀 비트(Spin Bit)

QUIC 워킹그룹에서 수백 개의 이메일을 주고받고 수십 시간의 토론을 걸친 가장 긴 설계 토론 중
하나가 단일 비트 즉, 스핀 비트(Spin Bit)에 관한 것이다.

이 스핀 비트를 지지하는 사람들은 두 QUIC 엔드포인트 사이에 있는 운영자나 사람들이
지연 시간을 측정할 필요가 있다고 주장한다.

이 기능을 반대하는 사람들은 잠재적인 정보 유출을 좋아하지 않았다.

## 비트 회전시키기

클라이언트와 서버 두 엔드포인트는 각 QUIC 연결에 대해 0 또는 1의 스핀 값을 유지하면서
해당 연결에 적절한 값으로 스핀 비트를 설정해서 패킷을 보낸다.

양 측은 한 라운드 트립동안 같은 값으로 설정된 스핀 비트를 가진 패킷을 보내고 이후 이 값을 토글한다.
이로 인해 비트 필드에 0과 1의 파동이 나타나고 관찰자가 이를 모니터링할 수 있다.

발송자가 애플리케이션도 아니고 제약된 흐름 제어도 아닌 경우에만 이 측정을 할 수 있고
네트워크에서 패킷의 순서가 재정리될 때도 데이터에 잡음이 낄 수 있다.
