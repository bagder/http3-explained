## Bloqueo de cabeza de línea TCP (_TCP head of line blocking_)

HTTP/2 se realiza sobre TCP y con muchas menos conexiones TCP que cuando se
utilizan versiones anteriores de HTTP. TCP es un protocolo para transferencias 
fiables y básicamente se puede pensar en él como una cadena imaginaria entre 
dos máquinas. Lo que se pone en la red en un extremo terminará en el otro,
en el mismo orden - eventualmente. (O la conexión se rompe).

![Una cadena TCP entre dos ordenadores](../images/tcp-chain.png)

Con HTTP/2, los navegadores típicos realizan decenas o cientos de transferencias
paralelas a través de una única conexión TCP.

Si un solo paquete se cae, o se pierde en la red en algún lugar entre dos puntos
finales que hablan HTTP/2, significa que toda la conexión TCP se detiene 
mientras el paquete perdido se retransmite y encuentra su camino hacia el 
destino. Dado que TCP es esta "cadena", significa que si un eslabón se pierde de
repente, todo lo que vendría después del eslabón perdido tiene que esperar.

Una ilustración utilizando la metáfora de la cadena al enviar dos flujos a 
través de esta conexión. Un flujo rojo y un flujo verde:

![La cadena mostrando los enlaces en diferentes colores](../images/tcp-chain-streams.png)

¡Se convierte en un bloqueo de cabeza de línea TCP!

A medida que aumenta la tasa de pérdida de paquetes, HTTP/2 rinde cada vez 
menos. Con un 2% de pérdida de paquetes (que es una calidad de red terrible, 
ojo), las pruebas han demostrado que los usuarios de HTTP/1 suelen estar mejor, 
porque  suelen tener hasta seis conexiones TCP entre las que distribuir los 
paquetes perdidos. Esto significa que por cada paquete perdido, las otras 
conexiones pueden continuar.

Arreglar este problema no es fácil, si acaso es posible, con TCP.

## Los flujos independientes evitan el bloqueo

Con QUIC todavía hay una configuración de conexión entre los dos puntos 
finales que hace que la conexión sea segura y la entrega de datos fiable.

![Una cadena QUIC entre dos ordenadores](../images/tcp-chain.png)

Cuando se establecen dos flujos diferentes sobre esta conexión, se tratan
de forma independiente, de manera que si se pierde algún enlace para uno 
de los flujos, sólo ese flujo, esa cadena en particular, tiene que hacer 
una pausa y esperar a que el enlace perdido se retransmita.

Ilustrado aquí con un flujo amarillo y otro azul enviados entre dos puntos 
finales.

![Dos flujos QUIC entre dos ordenadores](../images/quic-chain-streams.png)
