# Datos tempranos

QUIC ofrece handshakes de 0-RTT y 1-RTT que reducen el tiempo de negociación y 
establecimiento de una nueva conexión. Compárese con el handshake de 3 vías de 
TCP.

Además de eso, QUIC ofrece soporte de "datos tempranos" desde el principio que
se hace para permitir más datos y se utiliza más fácilmente que TCP Fast Open.

Con el concepto de flujo, se puede hacer otra conexión lógica al mismo host a la
vez sin tener que esperar a que la existente termine primero.

## TCP Fast Open es problemático

TCP Fast Open se publicó como [RFC 7413](https://tools.ietf.org/html/rfc7413) en
diciembre de 2014 y esa especificación describe cómo las aplicaciones pueden 
pasar datos al servidor para que se entreguen ya en el primer paquete TCP SYN.

El soporte real de esta característica en la naturaleza ha tomado tiempo y está 
plagado de problemas incluso hoy en 2018. Los implementadores de la pila TCP han
tenido problemas y también lo han tenido las aplicaciones que intentan 
aprovechar esta característica, tanto para saber en qué versión del sistema 
operativo intentar activarla como para averiguar cómo retroceder con gracia y
lidiar cuando surgen problemas. Se han identificado varias redes que interfieren
con el tráfico TFO y, por tanto, han arruinado activamente estos handshakes TCP.

