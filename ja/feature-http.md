## HTTP/3

HTTPレイヤは HTTP/2 における HPACK によく似た圧縮技術である QPACK を利用した HTTPヘッダ圧縮を内包し、
HTTP準拠のトランスポートを行います。

HPACKアルゴリズムはストリームの順序保証伝送に依存するため、修正せずに HTTP/3 で再利用することは不可能です。
これは QUIC の提供するストリームにおいては伝送がばらばらに行われるためです。
QPACK は [HPACK](https://httpwg.org/specs/rfc7541.html) の QUIC 対応版といえます。