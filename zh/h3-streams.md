# QUIC流与HTTP/3

HTTP/3是针对QUIC设计的，所以它可以使用QUIC流的所有好处。而HTTP/2不得不在TCP之上构建流和复用概念。

通过HTTP/3的HTTP请求使用一系列数据流。

## HTTP/3帧（frames）

HTTP/3建立一些QUIC数据流，并且发送一系列帧给对方。其中有一些固定的（八种）数据帧种类。最关键的帧包括：

- HEADERS：发送压缩的HTTP首部
- DATA：发送二进制数据
- GOAWAY：请关闭连接

## HTTP请求

客户端通过它发起的 *双向* QUIC流来传送HTTP请求。

一个请求包括一个HEADERS帧，之后可能有一两种其他的帧：一系列的DATA帧，和一个尾HEADERS帧。

发送请求后，客户端会关闭流。

## HTTP响应

服务器以单向流发送HTTP响应。含有一个HEADERS帧，一系列DATA帧，也许还有一个尾HEADERS帧。

## QPACK头部

HEADERS含有用QPACK算法压缩的HTTP头部。QPACK和HTTP/2中的HPACK（ [RFC
7541](https://httpwg.org/specs/rfc7541.html) ）类似，并针对乱序流进行了相应修改。

QPACK将在端点间建立两个单向QUIC流。它们被用于在两个方向上传递动态的表信息。
