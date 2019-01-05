# QUIC流与HTTP/3

HTTP/3针对QUIC设计，所以它可以利用QUIC流的所有好处。而HTTP/2不得不在TCP之上构建它的数据流和复用概念。

通过HTTP/3传输的HTTP请求使用一系列的数据流完成。

## HTTP/3帧（frame）

HTTP/3意味着建立QUIC数据流，并将一系列帧发送给对方。HTTP/3中的数据帧种类不多且固定（截至2018年12月18日有九种）。最关键的帧可能是：

- HEADERS：发送压缩的HTTP头部
- DATA：发送二进制数据内容
- GOAWAY：请关闭此连接

## HTTP请求

客户端通过其发起的 双向 QUIC流来发送HTTP请求。

一个请求包括一个HEADERS帧，之后可能有一两种其他的帧：一系列的DATA帧，以及可能有一个作为末尾的HEADERS帧。

发送一个请求后，客户端会关闭该数据流以进行发出。

## HTTP响应

服务器在双向流上发回其HTTP响应。其中含有一个HEADERS帧，一系列DATA帧，末尾可能有一个HEADERS帧。

## QPACK头部

HEADERS含有用QPACK算法压缩的HTTP头部。QPACK与HTTP/2中的HPACK（[RFC
7541](https://httpwg.org/specs/rfc7541.html)）类似，并针对乱序流做了相应修改。

QPACK本身在两个端点间使用两个额外的单向QUIC流，用于在两个方向上传递动态表信息。
