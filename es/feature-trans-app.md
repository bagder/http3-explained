## Nivel de transporte y aplicación

El protocolo IETF QUIC es un protocolo de transporte, sobre el que se pueden
utilizar otros protocolos de aplicación pueden ser utilizados. El protocolo
inicial de la capa de aplicación es HTTP/3 (h3).

La capa de transporte soporta conexiones y flujos.

La versión heredada de Google de QUIC tenía el transporte y HTTP pegados en una
sola y era un protocolo enviar-tramas-http/2-sobre-udp de propósito mas 
espécifico.
