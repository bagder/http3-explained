## HTTP/3

HTTP层以HTTP风格传输内容，包括使用QPACK进行HTTP头部压缩，这和HTTP/2中使用HPACK压缩头部类似。

HPACK算法依赖于数据流的 *有序* 交付，由于HTTP/3的数据流之间可能乱序，所以该算法需要修改才能使用。QPACK可以认为是适用于QUIC的 [HPACK](http://httpwg.org/specs/rfc7541.html)。
