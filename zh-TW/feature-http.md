## HTTP/3 over QUIC

HTTP 層稱為 HTTP/3，執行 HTTP 風格的傳輸，包括使用 QPACK 進行 HTTP 標頭壓縮 - 這和 HTTP/2 中使用 HPACK 壓縮標頭類似。

HPACK 算法依賴於串流的有序交付，由於 HTTP/3 的串流之間可能亂序，所以該算法需要修改才能使用。
QPACK 可被視為適用於 QUIC 版本的 [HPACK](https://httpwg.org/specs/rfc7541.html).
