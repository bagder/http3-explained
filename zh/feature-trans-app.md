## 传输层与应用层

IETF 版 QUIC 是一个传输层协议，在该协议之上可以运行其他应用层协议。初始的应用层协议是 HTTP/3（h3）。

传输层协议负责连接和数据流处理。

在 Google 的传统 QUIC 中，传输层与 HTTP 融在一起，为包揽一切的全功能设计，它是一个更有指向性的“基于 UDP 传输 HTTP/2 帧”（send-http/2-frames-over-udp）的协议。
