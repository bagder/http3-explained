## TLS 1.3

La seguridad de transporte utilizada en QUIC usa TLS 1.3 ([RFC 
8446](https://tools.ietf.org/html/rfc8446)) y nunca hay conexiones QUIC sin 
cifrar.

TLS 1.3 tiene varias ventajas en comparación con las versiones anteriores de 
TLS, pero una de las principales razones para usarlo en QUIC es que 1.3 cambió
el handshake para requerir menos viajes de ida y vuelta. Esto reduce la latencia
del protocolo.

La versión heredada de Google de QUIC utilizaba una criptografía personalizada.
