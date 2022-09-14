## HTTP/3 sobre QUIC

La capa HTTP, llamada HTTP/3, realiza transportes de estilo HTTP, incluyendo la
compresión de cabeceras HTTP usando QPACK - que es similar a la compresión 
HTTP/2 llamada HPACK.

El algoritmo HPACK depende de una entrega *ordenada* de flujos, por lo que no
fue posible reutilizarlo para HTTP/3 sin modificaciones, ya que QUIC ofrece 
flujos que pueden ser entregados fuera de orden. QPACK puede verse como la 
versión adaptada a QUIC de [HPACK](https://httpwg.org/specs/rfc7541.html).
