# 0-RTT

To reduce the time required to establish a new connection, a client that has previously
connected to a server may cache certain parameters from that connection and subsequently 
set up a **0-RTT** connection with the server. This allows the client to send data immediately,
without waiting for a handshake to complete.
