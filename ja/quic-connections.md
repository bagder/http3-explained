# コネクション

QUIC コネクションは2つの QUIC エンドポイント間の1対の対話です。 QUIC の接続の確立はバージョンネゴシエーションと暗号化および転送ハンドシェイクを組み合わせて、接続確立までの待ち時間を短縮します。

実際にデータをそのような接続に送信するには、1つまたはそれ以上のストリームを作成し、使用する必要があります。

## 接続ID

Each connection possesses a set of connection identifiers, or connection IDs,
each of which can be used to identify the connection. Connection IDs are
independently selected by endpoints; each endpoint selects the connection IDs
that its peer uses.

The primary function of these connection IDs is to ensure that changes in
addressing at lower protocol layers (UDP, IP, and below) do not cause packets
for a QUIC connection to be delivered to the wrong endpoint. 

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
