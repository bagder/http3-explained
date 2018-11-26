## 用TCP还是UDP

如果我们不能解决TCP队头阻塞问题，那么按道理，我们应该发明一个UDP和TCP之外的新的传输层协议。或者我们应该用IETF在 [RFC
4960](https://tools.ietf.org/html/rfc4960) 中定义的 [SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol) 标准，因为它符合我们的一些需求。

但是，近年来创建新的传输层协议基本都失败了，因为部署他们遇到了很大的阻力。用户和服务器之间要经过许多防火墙、NAT（地址转换）、路由器和其他中间设备（middle-box），这些设备有很多只认TCP和UDP。如果要用另一种传输层协议，那么就会有N%的连接建立不起来，因为这些中间设备认为除了TCP和UDP协议以外的协议都是不安全的。如此高的的失败率让我们放弃引入新的协议。

另外，传输层协议的改变一般意味着操作系统内核也需要修改。操作系统内核的修改非常缓慢，需要慢慢努力推进。这些年，IETF已经标准化过的TCP新特性中，因为操作系统支持问题，有好些特性好几年后都没有广泛部署。

## 为什么不在UDP上使用SCTP

SCTP是一个支持数据流的可靠传输层协议，而且WebRTC上面已经有基于UDP的实现。

这看上去很好，可是还不够好，跟QUIC相比，它：

- 没有解决数据流的队头阻塞问题
- 连接建立时需要指定数据流的数目
- TLS支持不够好
- 建立连接时候需要4次握手，而QUIC一次都不用
- QUIC是类TCP的字节流，SCTP是信息流（message-based）
- QUIC支持IP地址迁移，SCTP不行

想要了解更多SCTP和QUIC的差异，请参阅 [A Comparison between SCTP and QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00)
