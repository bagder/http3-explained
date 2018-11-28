## IETF

IETFによってプロトコルの標準化が始まり、QUICワーキンググループが発足した当初から、IETFはQUICはHTTP"だけ"ではなく、他のプロトコルにも適用し標準化しようと決定しました。Google-QUICはHTTPだけを対象にしていましたが、実際はHTTP/2のフレーム構文を利用し、HTTP/2でも効果的に動作していました。

また、IETF-QUICではGoogleが"カスタム"した手法ではなく、TLS 1.3に基づいた暗号化とセキュリティを取り入れることにしました。

send-more-than-HTTPという要求を満たすため、IETF QUICプロトコルのアーキテクチャは2つの異なるレイヤーに分割されました。"transport QUIC"レイヤーと"HTTP over QUIC"レイヤーです。(HTTP over QUICレイヤーは"hq"と呼ばれることがあります)

このレイヤー分割は、一見無害のようにも見えるが、IETF-QUICとGoogle-QUICで大きな差分を生み出しました。

ワーキンググループはQUICの最初のバージョンを適切なフォーカスで予定通りに提供するために、HTTPにフォーカスし、HTTPで無いものは後に回すことにしました。

私達がこの本を書き始めた2018年3月にはQUICバージョン1の仕様の最終盤は2018年11月にリリースされることになっていましたが、現在は延期されて2019年7月となっています。

IETF-QUICの作業が進みに連れ、GoogleチームはIETF版から詳細を組み込み、ゆっくりとIETF版が目指しているものをGoogle版にも取り入れ始めました。GoogleはGoogle版のQUICをGoogleのブラウザとサービスで動かし続けました。

[最新の実装](https://github.com/quicwg/base-drafts/wiki/Implementations)ではIETFバージョンにフォーカスしGoogleバージョンとの互換性はありません。
