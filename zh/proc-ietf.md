## IETF

IETF为QUIC标准化成立的QUIC工作组很快就决定，IETF标准化的QUIC协议应该支持HTTP以外的其他应用层协议。Google版的QUIC只传输HTTP——在实践中，它则被用来传输符合HTTP/2帧语义的片段。

另外，工作组最初也决定IETF-QUIC应该基于TLS 1.3进行加密与安全传输，而不使用Google版QUIC定制的方法。

为满足不局限于HTTP的传输需求，IETF QUIC协议的架构被分为两个独立的层：传输层QUIC和“基于QUIC的HTTP”（HTTP over QUIC）层。后者在2018年11月被重命名为HTTP/3。

尽管这种分层结构看似人畜无害，但这实质上造成IETF-QUIC与Google版QUIC有着诸多不同。

工作组很快发现了这一点，为保持适当关注和能按时交付第一版QUIC，工作组的重心转移到了先交付“基于QUIC的HTTP”传输部分，非HTTP传输部分将留待今后研究。

2018年3月，当我们开始写这本书的时候，第一版QUIC最终的规范计划于2018年11月发布。不过发布时间在这之后被推迟到了2019年7月。

在IETF-QUIC取得进展的同时，Google团队已经整合了IETF版本的细节并逐渐推进他们的协议版本，以期最终可能符合IETF定义的规范。尽管如此，Google在他们的浏览器和服务中继续使用自己的QUIC版本。

[正在开发的大多数新实现](https://github.com/quicwg/base-drafts/wiki/Implementations)
已经决定着眼于IETF版本，与Google版本并不兼容。
