# QUIC 流与 HTTP/3

HTTP/3 针对 QUIC 设计，所以它可以利用 QUIC 流的所有好处。而 HTTP/2 不得不在 TCP 之上构建它的数据流和复用概念。

通过 HTTP/3 传输的 HTTP 请求使用一系列的数据流完成。

## HTTP/3 帧（frame）

HTTP/3 意味着建立 QUIC 数据流，并将一系列帧发送给对方。HTTP/3 中的数据帧种类不多且固定（截至 2018 年 12 月 18 日有九种）。最关键的帧可能是：

- HEADERS：发送压缩的 HTTP 头部
- DATA：发送二进制数据内容
- GOAWAY：请关闭此连接

## HTTP 请求

客户端通过其发起的 双向 QUIC 流来发送 HTTP 请求。

一个请求包括一个 HEADERS 帧，之后可能有一两种其他的帧：一系列的 DATA 帧，以及可能有一个作为末尾的 HEADERS 帧。

发送一个请求后，客户端会关闭该数据流以进行发出。

## HTTP 响应

服务器在双向流上发回其 HTTP 响应。其中含有一个 HEADERS 帧，一系列 DATA 帧，末尾可能有一个 HEADERS 帧。

## QPACK 头部

HEADERS 含有用 QPACK 算法压缩的 HTTP 头部。QPACK 与 HTTP/2 中的 HPACK（[RFC
7541](https://httpwg.org/specs/rfc7541.html)）类似，并针对乱序流做了相应修改。

QPACK 本身在两个端点间使用两个额外的单向 QUIC 流，用于在两个方向上传递动态表信息。
