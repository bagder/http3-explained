## TCP o UDP

Si no podemos arreglar el bloqueo de cabecera en TCP, entonces en teoría 
deberíamos ser capaces de hacer un nuevo protocolo de transporte junto a UDP y 
TCP en la pila de la red. O quizás incluso utilizar 
[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol) que 
es un protocolo de transporte estandarizado por el IETF en [RFC 
4960](https://tools.ietf.org/html/rfc4960) con varias de las características
deseadas.

Sin embargo, en los últimos años los esfuerzos para crear nuevos protocolos de
transporte se han detenido casi por completo debido a las dificultades para 
desplegarlos en Internet. El despliegue de nuevos protocolos se ve obstaculizado
por muchos cortafuegos, NATs, routers y otras cajas intermedias que sólo
permiten TCP o UDP se despliegan entre los usuarios y los servidores que 
necesitan alcanzar. Introducir otro protocolo de transporte hace que el N% de 
las conexiones fallen porque están siendo bloqueadas por cajas que ven que no es
UDP o TCP y que, por tanto, es malo o erróneo de alguna manera. La tasa de 
fallos del N% se considera a menudo demasiado alta para que merezca la pena el 
esfuerzo.

Además, cambiar cosas en la capa de protocolo de transporte de la pila de red 
suele significar protocolos implementados por los kernels del sistema operativo.
Actualizar y desplegar nuevos kernels de los sistemas operativos es un proceso
lento que requiere un esfuerzo considerable. Muchas de las mejoras de TCP
estandarizadas por el IETF no están ampliamente desplegadas o utilizadas porque
no están ampliamente soportadas.

## Por qué no SCTP-sobre-UDP

SCTP es un protocolo de transporte fiable con flujos, y para WebRTC 
hay incluso implementaciones existentes que lo utilizan sobre UDP.

Esto no se consideró lo suficientemente bueno como una alternativa a QUIC debido
a varias razones, incluyendo:

 - SCTP no soluciona el problema del bloqueo de la cabeza de línea para los flujos
 - SCTP requiere que el número de flujos se decida al establecer la conexión
 - SCTP no tiene una historia sólida de TLS/seguridad
 - SCTP tiene un handshake de 4 vías, QUIC ofrece 0-RTT
 - QUIC es un bytestream como TCP, SCTP está basado en mensajes
 - Las conexiones QUIC pueden migrar entre direcciones IP, pero SCTP no

Para más detalles sobre las diferencias, véase [A Comparison between SCTP and
QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).
