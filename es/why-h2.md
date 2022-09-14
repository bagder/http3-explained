## ¿Te acuerdas de HTTP/2?

La especificación de HTTP/2 [RFC 7540](https://httpwg.org/specs/rfc7540.html)
fue publicado en mayo de 2015 y desde entonces el protocolo se ha implementado
y desplegado ampliamente en Internet y en la World Wide Web.

A principios de 2018, casi el 40% de los principales 1000 sitios web ejecutan 
HTTP/2, alrededor del 70% de todas las solicitudes HTTPS que emite Firefox 
obtienen respuestas HTTP/2 y todos los principales navegadores, servidores y 
proxies lo soportan.

HTTP/2 aborda toda una serie de deficiencias de HTTP/1 y con la introducción
de la segunda version de HTTP los usuarios pueden dejar de utilizar un montón
de métodos alternativos. Algunos de las cuales son bastante agobiante para los
desarrolladores web.

Una de las principales características de HTTP/2 es que hace uso de la 
multiplexación, de modo que que muchos flujos lógicos (_streams_) se envían a
través de la misma conexión TCP física. Esto hace que muchas cosas sean mejores 
y más rápidas. Hace que el control de la congestión funcione mucho mejor, 
permite a los usuarios usar TCP mucho mejor y así saturar adecuadamente el 
ancho de banda, hace que las conexiones TCP sean más duraderas, lo que es bueno
para que para que puedan alcanzar su máxima velocidad con más frecuencia que 
antes. La compresión de cabeceras hace que se utilice menos ancho de banda.

Con HTTP/2, los navegadores suelen utilizar *una* conexión TCP a cada host en
lugar de de las *seis* anteriores. De hecho, las técnicas de coalescencia de la
conexión y de "desharding" utilizadas con HTTP/2 pueden incluso reducir el 
número de conexiones mucho más que eso.

HTTP/2 solucionó el problema de bloqueo de la cabecera de la línea HTTP 
(_HTTP head of line blocking_), donde los clientes tenían que esperar a que
terminara la primera petición (_request_) para que pudiera salir la siguiente.

![http2 man](../images/h2-man.jpg)
