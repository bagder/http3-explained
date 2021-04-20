## 用 TCP 还是 UDP

如果我们无法解决 TCP 内的队头阻塞问题，那么按道理，我们应该在网络栈中发明一个 UDP 和 TCP 之外的新型传输层协议。或者我们应该用 IETF 在 [RFC
4960](https://tools.ietf.org/html/rfc4960) 中标准化的 [SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol) 传输层协议，它也有多个我们所需的特征。

但在近些年来，因为在互联网上部署遭遇很大的困难，创造新型传输层协议的努力基本上都失败了。用户与服务器之间要经过许多防火墙、NAT（地址转换）、路由器和其他中间设备（middle-box），这些设备有很多只认 TCP 和 UDP。如果使用另一种传输层协议，那么就会有 N%的连接无法建立，这些中间设备会认为除 TCP 和 UDP 协议以外的协议都是不安全或者有问题的。如此高的的失败率一般被认为不值得再做出努力。

另外，网络栈中的传输层协议改动一般意味着操作系统内核也要做出修改。更新和部署新款操作系统内核的过程十分缓慢，需要付出很大的努力。由 IETF 标准化的许多 TCP 新特性都因缺乏广泛支持而没有得到广泛的部署或使用。

## 为什么不基于 UDP 使用 SCTP

SCTP 是一个支持数据流的可靠的传输层协议，而且在 WebRTC 上已有基于 UDP 的对它的实现。

这看上去很好，但与 QUIC 相比还不够好，它：

- 没有解决数据流的队头阻塞问题
- 连接建立时需要决定数据流的数量
- 没有稳固的 TLS/安全性支持
- 建立连接时候需要 4 次握手，而 QUIC 一次都不用（0-RTT）
- QUIC 是类 TCP 的字节流，而 SCTP 是信息流（message-based）
- QUIC 连接支持 IP 地址迁移，SCTP 不行

若要了解更多 SCTP 与 QUIC 的差异，请参阅 [A Comparison between SCTP and QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00)
