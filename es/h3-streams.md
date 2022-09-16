# Flujos de QUIC y HTTP/3

HTTP/3 está hecho para QUIC, por lo que aprovecha al máximo los flujos de QUIC,
mientras que HTTP/2 tuvo que diseñar su propio concepto de flujo y
multiplexación sobre TCP.

Las peticiones HTTP realizadas sobre HTTP/3 utilizan un conjunto específico de
flujos.

## Tramas de HTTP/3

HTTP/3 implica la creación de flujos QUIC y el envío de un conjunto de tramas al
otro extremo. Sólo hay un pequeño número fijo (¡en realidad nueve al 18 de
diciembre de 2018!) de tramas conocidas en HTTP/3. Las más importantes son
probablemente

- HEADERS, que envía cabeceras HTTP comprimidas
- DATA, envía contenidos de datos binarios
- GOAWAY, que cierra esta conexión

## Solicitud HTTP

El cliente envía su petición HTTP en un flujo QUIC *bidireccional* iniciado por
el cliente.

Una petición consiste en una única trama HEADERS y, opcionalmente, puede ir
seguida de una o dos tramas más: una serie de tramas DATA y posiblemente una
última trama HEADERS para los trailers.

Después de enviar una petición, un cliente cierra el flujo para su envío.

## Respuesta HTTP

El servidor devuelve su respuesta HTTP en el flujo bidireccional. Una trama
HEADERS, una serie de tramas DATA y posiblemente una trama HEADERS final.

## Cabeceras QPACK

Las tramas HEADERS contienen cabeceras HTTP comprimidas mediante el algoritmo
QPACK. QPACK es similar en estilo a la compresión HTTP/2 llamada HPACK (
[RFC 7541](https://httpwg.org/specs/rfc7541.html)), pero modificada para
trabajar con flujos entregados fuera de orden.

QPACK utiliza dos flujos QUIC unidireccionales adicionales entre los dos puntos
finales. Se utilizan para transportar información de la tabla dinámica en
cualquier dirección.
