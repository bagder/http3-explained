# Las conexiones utilizan TLS

Inmediatamente después del paquete inicial que establece una conexión, el 
iniciador envía una trama criptográfica que comienza a configurar el handshake 
de la capa segura. La capa de seguridad capa de seguridad utiliza la seguridad
TLS 1.3.

No hay forma de optar por no utilizar TLS en una conexión QUIC. El protocolo 
está diseñado para que sea difícil de manipular por las cajas intermedias, con
el fin de para ayudar a prevenir la osificación del protocolo.
