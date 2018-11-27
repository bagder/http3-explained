## 传输层与应用层协议

IETF版QUIC是一个传输层协议，在其之上运行着应用层协议。最初的应用层协议是HTTP/3（h3）。

传输层协议负责连接和数据流处理。

谷歌旧版QUIC的传输层和HTTP是混在一起的更专注的全能协议，这个协议叫“用UDP传HTTP/2”（send-http/2-frames-over-udp）。
