## IETF

為標準化 IETF 中協定而成立的 QUIC 工作組很快就決定了，除了 HTTP 應用層協定以外，QUIC 還應該能夠支援傳輸其他協定。
Google 版的 QUIC 僅用於 HTTP - 但實際上使用了 HTTP/2 框架語法，並與 HTTP/2 兼容。

另外，還決定採用基於 TLS 1.3 的加密和安全性，而不是 Google 的 "自定義" 方法。

為了滿足不局限於 HTTP 的傳輸需求，IETF QUIC 協定的架構被分為兩個獨立的層：
傳輸層 QUIC 和 "基於 QUIC 的 HTTP"（ HTTP over QUIC ）層（ 有時縮寫為 "hq" ）。

乍看之下這種分層似乎無害，但在 IETF-QUIC 和 Google-QUIC 之間卻有很大的不同。

工作組很快就發現了這點，為保持適當關注和能按時交付第一版 QUIC，工作組將重心轉移到了 HTTP 傳輸，非 HTTP 的傳輸將留待今後研究。

在 2018 年 3 月，當我們開始編寫本書時，工作組計劃是在 2018 年 11 月發布 QUIC 第ㄧ版的最終規範，不過目前已經延遲了多次，在撰寫本文時（ 2020 年 6 月 ）工作組正在進入最終定稿階段。

隨著有關 IETF-QUIC 的工作的進行，Google 團隊已經整合了 IETF 版本的細節並逐漸推進他們的協定版本，以便能符合 IETF 定義的規範。
Google 繼續在其瀏覽器和服務上運行 Google 版本的 QUIC。

[正在開發的大多數新實作](https://github.com/quicwg/base-drafts/wiki/Implementations) 已決定專注於 IETF 版本，並且與Google 版本不兼容。
