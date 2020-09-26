## 回顧 HTTP/2

自 HTTP/2 規範 [RFC 7540](https://httpwg.org/specs/rfc7540.html) 於2015年5月發布以來，此協定已在 Internet 和 World Wide Web 上廣泛的實作和部署。

在2018年初，排名前 1000 位的網站中有 40％ 運行於 HTTP/2，在 Firefox 發出的請求中，大約 70％ 的 HTTPS 請求得到了 HTTP/2 的回應，且所有主要瀏覽器，服務器和代理器也都支援 HTTP/2。

HTTP/2 解決了 HTTP/1 中的許多缺點，隨著第二版 HTTP 的導入，用戶可以停止使用許多不必要的 workarounds。
這些 workarounds 有一部分對於 Web 開發人員來說負擔很重。

HTTP/2 的主要特徵之一是它利用了多工（ multiplexing )，因此許多邏輯流是通過同一個 TCP 連接發送的，這使很多事情變得更好更快。
它使擁塞（ congestion ) 控制運作的更好，它使用戶可以更好地使用 TCP，更充分的使用頻寬，更長久的 TCP 連接 - 這樣做的好處是，它們比以前更頻繁地達到全速運行。標頭壓縮使其能使用較少的頻寬。

使用 HTTP/2 時，瀏覽器通常對每個主機使用 *一個* TCP 連接，而不是先前的 *六個*。
實際上，與 HTTP/2 一起使用的連接合併（ connection coalescing ）和 "去分片" 技術實際上可以減去更多的連接。

HTTP/2 解決了 HTTP 隊頭阻塞的問題，即客戶端必須等待隊中的第一個請求完成，才能發出下一個請求。

![http2 man](../images/h2-man.jpg)
