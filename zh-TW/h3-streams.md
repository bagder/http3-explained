# QUIC 串流及 HTTP/3

HTTP/3 是為 QUIC 設計的，因此它能利用 QUIC 的好處，而 HTTP/2 不得不在 TCP 上建構它的串流和復用概念。

通過 HTTP/3 傳輸的 HTTP 請求是使用一系列特定的串流完成。

## HTTP/3 frames

HTTP/3 代表著建立 QUIC 串流，並將一系列 frame 發送給對方。 HTTP/3 中的數據 frame 種類不多且固定（ 截至 2018 年 12 月 18 日有九種）。其中最重要的 frame 是：

- HEADERS, 發送壓縮的 HTTP 標頭
- DATA, 發送二進制資料內容
- GOAWAY, 請關閉此連接

## HTTP Request

客戶端通過其發起的 *雙向* QUIC 串流來發送 HTTP 請求。

一個請求由單個 HEADERS frame 組成，並可以選擇後面跟隨一個或兩個 frame：
一系列的 DATA frame，以及可能有一個作為末尾的 HEADERS frame。

發送一個請求後，客戶端會關閉該串流以進行發出。

## HTTP Response

伺服器端在雙向串流上發回其 HTTP 回應。其中含有一個 HEADERS frame，一系列 DATA frame，末尾可能有一個 HEADERS frame。

## QPACK headers

HEADERS 含有用 QPACK 算法壓縮的 HTTP 標頭。 QPACK 與 HTTP/2 中的 HPACK ([RFC7541](https://httpwg.org/specs/rfc7541.html)) 類似，並針對亂序串流做了對應的修改。

QPACK 本身在兩個端點之間使用了兩個附加的單向 QUIC 流。 它們用於在任一方向上傳送動態表訊息。
