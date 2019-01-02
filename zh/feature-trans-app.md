## 传输层与应用层

IETF版QUIC是一个传输层协议，在该协议之上可以运行其他应用层协议。初始的应用层协议是HTTP/3（h3）。

传输层协议负责连接和数据流处理。

在Google的传统QUIC中，传输层与HTTP融在一起，为包揽一切的全功能设计，它是一个更有指向性的“基于UDP传输HTTP/2帧”（send-http/2-frames-over-udp）的协议。
