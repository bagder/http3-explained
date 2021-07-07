## IETF

IETF 为 QUIC 标准化成立的 QUIC 工作组很快就决定，IETF 标准化的 QUIC 协议应该支持 HTTP 以外的其他应用层协议。Google 版的 QUIC 只传输 HTTP——在实践中，它则被用来传输符合 HTTP/2 帧语义的片段。

另外，工作组最初也决定 IETF-QUIC 应该基于 TLS 1.3 进行加密与安全传输，而不使用 Google 版 QUIC 定制的方法。

为满足不局限于 HTTP 的传输需求，IETF QUIC 协议的架构被分为两个独立的层：传输层 QUIC 和“基于 QUIC 的 HTTP”（HTTP over QUIC）层。后者在 2018 年 11 月被重命名为 HTTP/3。

尽管这种分层结构看似人畜无害，但这实质上造成 IETF-QUIC 与 Google 版 QUIC 有着诸多不同。

工作组很快发现了这一点，为保持适当关注和能按时交付第一版 QUIC，工作组的重心转移到了先交付“基于 QUIC 的 HTTP”传输部分，非 HTTP 传输部分将留待今后研究。

2018 年 3 月，当我们开始写这本书的时候，第一版 QUIC 最终的规范计划于 2018 年 11 月发布。不过发布时间在这之后被推迟到了 2019 年 7 月。

在 IETF-QUIC 取得进展的同时，Google 团队已经整合了 IETF 版本的细节并逐渐推进他们的协议版本，以期最终可能符合 IETF 定义的规范。尽管如此，Google 在他们的浏览器和服务中继续使用自己的 QUIC 版本。

[正在开发的大多数新实现](https://github.com/quicwg/base-drafts/wiki/Implementations)
已经决定着眼于 IETF 版本，与 Google 版本并不兼容。
