## TLS 1.3

QUIC 中使用的傳輸層安全協定是 TLS 1.3 ([RFC8446](https://tools.ietf.org/html/rfc8446)) QUIC 没有任何非加密的連線。

與更早的 TLS 版本相比，TLS 1.3 有許多優點，但使用它的最主要原因是其握手所花費的往返次數更低，從而能降低協定的延遲。

Google 舊版的 QUIC 使用一個自定義的加密法。
