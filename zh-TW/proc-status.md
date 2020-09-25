# 目前的狀況

QUIC 工作組自 2016 年末以來一直在努力製定協定，在撰寫本文時（ 2020 年 6 月 ）已接近最後階段。

在 2019 年和 2020 年間，使用 HTTP/3 進行互操作性測試的數量不斷增加 [https://docs.google.com/spreadsheets/d/1D0tW89vOoaScs3IY9RGC0UesWGAwE6xyLk0l4JtvTVg/edit#gid=1268516408] CDN 和瀏覽器已經開始提供初始的支持 - 儘管它們通常會進度落後。

QUIC 工作組的 Wiki 頁面上有更多的資訊。 [QUIC implementations listed](https://github.com/quicwg/base-drafts/wiki/Implementations)

實現 QUIC 並不容易，到目前為止，協定本身還在不斷演變中。

## 伺服器端

NGINX 對 QUIC 和 HTTP/3 的支援正在開發中，並且 [已發布預覽版](https://www.nginx.com/blog/introducing-technology-preview-nginx-support-for-quic-http-3/).

至於 Apache 對 QUIC 的支援則是還沒有公開的聲明。

## 客戶端

尚未有任何主流瀏覽器供應商在任何狀態下提供可以運行 IETF 版本的 QUIC 或 HTTP/3 協定。

多年來，Google 瀏覽器一直在提供 Google 自己的 QUIC 版本，並且最近已經開始支持 IETF 版本。
Firefox 同樣之後會開始支援。

curl 在 2019 年 9 月 11 日發布了 7.66.0 版本中的第一個實驗性的 HTTP/3 支援（draft-22）。
curl 使用 Cloudflare 的 Quiche 或 ngtcp2 來完成工作。

## 實作的障礙

QUIC 決定使用 TLS 1.3 作為加密和安全層的基礎來避免發明新的東西，且依靠可信賴的現有協定。
不過工作組決定大幅精簡 QUIC 中 TLS 的使用，只使用 "TLS訊息"（ TLS Messages ）而不是協定中的 "TLS記錄"（ TLS Records ）。

這聽起來像是一個無害的更改，但實際上已對許多 QUIC 堆疊的實作者造成了重大障礙。
現存的支持 TLS 1.3 的 TLS libraries 都沒有提供此功能的 API 並允許 QUIC 訪問它。
有一些 QUIC 的實作由大型機構完成，這些機構可能有自己的 TLS 堆疊，但並不是所有人都能做到這種地步。

例如，占主導地位的開源重量級 OpenSSL 對此沒有任何 API。 解決此問題的計劃可能以在他們的 [PR8797](https://github.com/openssl/openssl/pull/8797) 中，它們計畫一種與 BoringSSL 非常相似的 API。

由於 QUIC 堆疊將需要基於其他 TLS libraries，使用單獨的修補 OpenSSL 構建或需要更新到將來的 OpenSSL 版本，這些最終也將導致部署障礙。
 
## 作業系统核心、CPU 負載

Google 和 Facebook 都提到，他們的 QUIC 大規模部署所需的 CPU 數量大約是通過 TLS 提供 HTTP/2 時相同流量負載的兩倍。

進一步的解釋

- 主要是 Linux 中的 UDP 部分根本沒有像 TCP 堆疊那樣優化，因為傳統上它沒有像這樣被用於高速傳輸。

- TCP 和 TLS 有硬體加速（負載卸載到硬體，offload），而這對於 UDP 很罕見，對於 QUIC 則基本上不存在。

就上述理由，我們可以相信 QUIC 的 CPU 使用量能隨著時間得到改善。
