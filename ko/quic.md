<!--
# How QUIC works

Without explaining the exact bits and bytes on the wire, this section describes how
the fundamental building blocks of the QUIC transport protocol work. If you want to
implement your own QUIC stack, this description should give you a general
understanding, but for all the details, refer to the actual IETF Internet Drafts
and RFCs.

1. Set up a [connection](quic-connections.md)
2. ... that includes [TLS security](quic-tls.md)
3. Then use [streams](quic-streams.md)
-->

# QUIC의 동작 방식

이번 장에서는 QUIC 전송 프로토콜의 기본적인 구성 요소가 어떻게 동작하는지를 설명한다.
QUIC 스택을 직접 구현하고자 한다면 이 책의 설명을 통해 전반적인 내용을 이해할 수는 있지만,
세부 내용은 IETF의 인터넷 드래프트와 RFC를 참고하기 바란다.

1. [연결](quic-connections.md)을 설정한다.
2. 여기에는 [TLS 보안](quic-tls.md)이 포함되어 있다.
3. [스트림](quic-streams.md)을 사용한다.
