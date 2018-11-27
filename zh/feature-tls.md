## TLS 1.3

QUIC使用TLS 1.3传输层安全协议（[RFC 8446](https://tools.ietf.org/html/rfc8446)）。QUIC没有非加密的版本。 

相比旧的TLS版本，TLS 1.3有很多改进，但使用它的最主要原因是握手所消耗的往返降低了。这会降低协议的延迟。

谷歌的旧版QUIC使用一个自己开发的加密协议。
