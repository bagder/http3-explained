## 傳輸層與應用層

IETF 的 QUIC 是一個傳輸層協定，在該協定之上可以運行其他應用層協定。初始的應用層協定是 HTTP/3（ h3 ）。

傳輸層協定負責連接和串流的處理。

在Google 舊版 QUIC 中，已將傳輸和 HTTP 粘合在一起，成為一個單一的 "do-it-all" 工具。
它的用途更加特殊，是一個更有指向性的 send-http/2-frames-over-udp 的協定。
