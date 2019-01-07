## TLS 1.3

QUIC使用TLS 1.3传输层安全协议（[RFC 8446](https://tools.ietf.org/html/rfc8446)）。QUIC没有非加密的版本。

与更早的TLS版本相比，TLS 1.3有着很多优点，但使用它的最主要原因是其握手所花费的往返次数更低，从而能降低协议的延迟。

Google的传统QUIC使用一个自行定制的加密法。
