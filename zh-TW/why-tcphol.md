## TCP 隊頭阻塞（ head of line blocking ）

HTTP/2 是基於 TCP 實作的。對比早期的 HTTP 版本，HTTP/2 使用的 TCP 連接數少了很多。
TCP 是一個可靠的通訊協定，基本上，你可以將它視為在兩台機器間建立的一個虛擬鏈，由其中一端放置於網路上的內容，最終總會以相同的順序出現在另一端。（ 或者遭遇連接中斷 ）

![a TCP chain between two computers](../images/tcp-chain.png)

採用 HTTP/2 時，典型的瀏覽器通過單個 TCP 連接進行數十或數百個並行傳輸。

如果 HTTP/2 連接雙方的網路中有一個封包丟失，或者任何一方的網路出現中斷，整個TCP連接就會暫停，丟失的封包需要被重新傳輸。
因為 TCP 是一個按序傳輸的鏈，因此，如果其中一個點丟失了，在該點之後的所有內容將陷入等待。

如下圖所示，我們用鏈條來表現一個連接上發送的兩個傳輸流，紅色與綠色的傳輸流：

![the chain showing links in different colors](../images/tcp-chain-streams.png)

這種單一封包造成的阻塞，就是所謂 TCP 上的對頭阻塞（ head of line blocking ）!

隨著封包遺失機率的增加，HTTP/2 的表現將越來越差。在2%的封包丟失率下（ 一個很差的網路環境 ），測試結果顯示 HTTP/1 用戶的性能更好，因為 HTTP/1 一般有六個TCP連接能夠分配處理丟失的封包，就算其中一個連接阻塞了，其他連接仍然可以繼續進行傳輸。

即使有可能，使用TCP修復此問題也並非想像中容易。

## 獨立的資料串流避免阻塞

使用 QUIC 時，兩個終端間仍建立一個連接，該連接也經過協商使得資料得到安全且可靠的傳輸。

![a QUIC chain between two computers](../images/tcp-chain.png)

但是，當我們在這個連接上建立兩個不同的資料串流時，它們將被視為互相獨立。也就是說，如果其中一個資料串流遺失封包了，那只有該資料串流必須停下來，然後等待重傳。

下面為兩終端間的示意圖，黃色與藍色是兩個獨立的資料串流。

![two QUIC streams between two computers](../images/quic-chain-streams.png)
