<!--
# Connections use TLS

Immediately after the initial packet setting up a connection, the initiator
sends a crypto frame that starts setting up the secure layer handshake. The
security layer uses TLS 1.3 security.

There is no way to opt-out or avoid using TLS for a QUIC connection. The
protocol is designed to be hard for middle-boxes to tamper with, in order
to help prevent ossification of the protocol.
-->

# TLS을 사용하는 연결

초기 패킷이 연결을 설정하자마자 초기화하는 쪽에서 보안 계층 핸드쉐이크의 설정을 시작하는
암호화 프레임을 보낸다. 보안 계층은 TLS 1.3 보안을 사용한다.

QUIC 연결에서에는 반드시 TLS를 사용해야 한다. QUIC 프로토콜은 프로토콜 경화를 방지하기 위해
미들박스가 조작하기 어렵게 설계되었다.
