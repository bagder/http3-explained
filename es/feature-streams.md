## Múltiples flujos dentro de las conexiones

Al igual que SCTP, SSH y HTTP/2, QUIC presenta flujos lógicos separados dentro
de las conexiones físicas. Una serie de flujos paralelos que pueden transferir
datos simultáneamente a través de una única conexión sin afectar a los otros 
flujos.

Una conexión es una configuración negociada entre dos end-points, similar a cómo
funciona una conexión TCP. Una conexión QUIC se realiza con un puerto UDP y una
dirección IP, pero una vez establecida la conexión se asocia por su "ID de 
conexión".

A través de una conexión establecida, cualquiera de las partes puede crear 
flujos y enviar datos al otro extremo. Los flujos se entregan en orden y son
fiables, pero diferentes flujos pueden entregarse fuera de orden.

QUIC ofrece control de flujo tanto en la conexión como en los flujos.

Ver más detalles en las secciones [conexiones](quic-connections.md) y 
[flujos](quic-streams.md)
