## TCP 還是 UDP

如果我們無法解決 TCP 中的隊頭阻塞問題，那麼從理論上來說，我們應該能夠在網路堆疊（ network
stack ）中建立一個 UDP 和 TCP 之外的新傳輸協定。甚至使用 [SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol) 這是 IETF 在 RFC 中標準化的傳輸協定 [RFC4960](https://tools.ietf.org/html/rfc4960) ，它也擁有我們需要的幾項特質。

但是近年來，由於在 Internet 上部署它們十分困難，幾乎完全停止了建立新傳輸協定的工作。
許多防火牆、NAT、路由器和其它中間設備（ middle-boxes ）阻礙了新協定的部署，這些防火牆和設備僅認得 TCP 或 UDP。
所以導入新的傳輸協定會使 N％ 的連接失效，因為它將會被這些設備所阻擋，因為它被視為不是 UDP 或 TCP（ 被視為不安全的協定 ）。
N％ 的失敗率被認為太高，不值得花費時間努力。

此外，更改網路堆疊的傳輸協定層中的內容通常表示該協定是由作業系統的核心所實作。更新和部署新的作業系統核心是一個緩慢的過程，需要大量的精力。由 IETF 標準化的許多 TCP 改進並未得到廣泛部署或使用，因為它們沒有得到廣泛支持。

## 為何不實作基於 UDP 的 SCTP

SCTP 是一個支持資料串流的可靠傳輸層協定，且在 WebRTC 上已有基於 UDP 的對它的實作。

但跟 QUIC 比較起來它還不夠好，原因如下：

 - SCTP 沒有解決資料串流的隊頭阻塞問題
 - SCTP 建立連接時就需要決定資料串流的數量
 - SCTP 沒有穩固的 TLS / 安全性支持
 - SCTP 建立連接時需要進行4-way handshake，QUIC 一次都不需要（ 0-RTT ）
 - QUIC 是類 TCP 的 bytestream，而 SCTP 是訊息流（ message-based ）
 - QUIC 連接可以在 IP 位址間遷移，SCTP 不行

更多 SCTP 與 QUIC 的差異，請參見 [A Comparison between SCTP and QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).
