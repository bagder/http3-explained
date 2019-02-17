<!--
# Connections

A QUIC connection is a single conversation between two QUIC endpoints. QUIC's
connection establishment combines version negotiation with the cryptographic
and transport handshakes to reduce connection establishment latency.

To actually send data over such a connection, one or more streams have to be
created and used.

## Connection ID

Each connection possesses a set of connection identifiers, or connection IDs,
each of which can be used to identify the connection. Connection IDs are
independently selected by endpoints; each endpoint selects the connection IDs
that its peer uses.

The primary function of these connection IDs is to ensure that changes in
addressing at lower protocol layers (UDP, IP, and below) do not cause packets
for a QUIC connection to be delivered to the wrong endpoint.

By taking advantage of the connection ID, connections can thus migrate between
IP addresses and network interfaces in ways TCP never could. For instance,
migration allows an in-progress download to move from a cellular network connection
to a faster wifi connection when the user moves their device into a location
offering wifi. Similarly, the download can proceed over the cellular connection
if wifi becomes unavailable.

## Port numbers

QUIC is built atop UDP, so a 16 bit port number field is used to differentiate
incoming connections.

## Version negotiation

An QUIC connection request originating from a client will tell the server
which QUIC protocol version it wants to speak, and the server will respond
with a list of supported versions for the client to select from.
-->

# 연결

QUIC 연결은 두 QUIC 엔드포인트 사이의 대화이다. QUIC의 연결 설정이 버전 협상, 암호화,
전송 핸드쉐이크로 구성되어 있으므로 연결 설정의 지연시간을 줄여준다.

이러한 연결을 통해 실제 데이터를 보내려면 하나 이상의 스트림을 만들어서 사용해야 한다.

## 연결 ID

각 연결은 연결 식별자나 연결 ID를 가지므로 이를 통해 연결을 식별한다. 엔드포인트가 자유롭게
연결 ID를 선택한다. 각 엔드포인트는 엔드포인트의 피어가 사용할 연결 ID를 선택한다.

이 연결 ID의 주요 기능은 하위 프로토콜 계층(UDP, IP 혹은 그 아래 계층)에서 주소가 변경되더라도
QUIC 연결의 패킷이 잘못된 엔드포인트로 전달되지 않도록 보장하는 것이다.

연결 ID를 이용하면 TCP에서는 불가능했던 방법으로 IP 주소와 네트워크 인터페이스 사이에서
연결이 마이그레이션 할 수 있다. 예를 들면 사용자가 자신의 기기를 들고 wifi가 지원되는 곳으로
이동했을 때 다운로드를 진행하면서 셀룰러 네트워크 연결에서 더 빠른 wifi 연결로 변경되는 것이
이 마이그레이션을 통해 가능하다. 마찬가지로 다운로드 wifi를 이용할 수 없게 되었을 때
셀룰러 연결을 통해 다운로드를 진행할 수 있다.

## 포트 번호

QUIC이 UDP 위에 만들어졌으므로 들어오는 연결을 구분하기 위해 16비트 포트 번호 필드를 사용한다.

## 버전 협상

클라이언트는 QUIC 연결 요청에서 어떤 QUIC 프로토콜 버전으로 통신하고 싶은지 서버에게 알려주고
서버는 클라이언트가 선택할 수 있도록 지원하는 버전 목록을 응답한다.
