## HTTP/3

HTTP 层以 HTTP 风格传输内容，包括使用 QPACK 进行 HTTP 头部压缩——这和 HTTP/2 中使用 HPACK 压缩头部类似。

HPACK 算法依赖于数据流的有序交付，由于 HTTP/3 的数据流之间可能乱序，所以该算法需要修改才能使用。QPACK 可被视作适用于 QUIC 版本的 [HPACK](https://httpwg.org/specs/rfc7541.html)。
