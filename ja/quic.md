# QUIC の仕組み

ワイヤ上( 伝送路の意) でのビットやバイトに関して詳細な説明はしませんが、
このセクションでは QUIC トランスポートプロトコルの基本的なビルディングブロックがどのように機能するのかを説明します。
独自に QUIC スタックを実装する場合でも、この説明によって理解を深めることが出来ますが、詳細については IETF のインターネットドラフトと RFC を参照してください。

1. Setup a [connection](quic-connections.md)
2. ... that includes [TLS security](quic-tls.md)
3. Then use [streams](quic-streams.md)
