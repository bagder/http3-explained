# コネクション

QUIC コネクションは2つの QUIC エンドポイント間の1対の対話です。 QUIC の接続の確立はバージョンネゴシエーションと暗号化および転送ハンドシェイクを組み合わせて、接続確立までの待ち時間を短縮します。

実際にデータをそのような接続を介して送信するには、1つかそれ以上のストリームを作成し使用する必要があります。

## 接続ID

それぞれの接続は1つの接続識別子か接続IDのセットを所有していて、接続を識別するためにそれぞれが使用することができます。接続IDはエンドポイントにより独立して選ばれます。各エンドポイントはピアが使用する接続IDを選択します。

これらの接続IDの主な機能は下位のプロコトル層(UDP, IP, 及びそれ以下)でのアドレッシングの変更が QUIC 接続のパケットを間違ったエンドポイントに配信しないようにすることです。

By taking advantage of the connection ID, connections can thus migrate between
IP addresses and network interfaces in ways TCP never could.

## ポート番号

QUIC is modeled on top of UDP so there is a 16 bit port number field to use to
differentiate incoming connection attempts with.

## バージョンネゴシエーション

An QUIC connection request originating from a client will tell the server
which QUIC protocol version it wants to speak, and the server will respond
with a list of supported versions for the client to select from when going
forward.
