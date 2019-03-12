<!--
# 0-RTT

To reduce the time required to establish a new connection, a client that has previously
connected to a server may cache certain parameters from that connection and subsequently
set up a **0-RTT** connection with the server. This allows the client to send data immediately,
without waiting for a handshake to complete.
-->

# 0-RTT

새로운 연결을 설정하는데 필요한 시간을 줄이려고 이전에 서버에 연결했던 클라이언트는 해당 연결의
특정 파라미터를 캐시한 뒤 이어서 서버와 **0-RTT** 연결을 설정할 수 있다. 이로 인해서 클라이언트는
핸드쉐이크가 완료되기를 기다리지 않고 바로 데이터를 보낼 수 있다.
