# Push del servidor HTTP/3

HTTP/3 server push es similar a lo descrito en HTTP/2 ([RFC 7540]
(https://httpwg.org/specs/rfc7540.html)), pero utiliza mecanismos diferentes. 

Un push de servidor es efectivamente la respuesta a una petición que el cliente
nunca envió.

Los push del servidor sólo se permiten si la parte del cliente los ha aceptado.
En HTTP/3 el cliente incluso establece un límite para el número de pushes que
acepta, informando al servidor de cuál es el ID máximo del flujo de push.
Sobrepasar ese límite provocará un error de conexión.

Si el servidor considera probable que el cliente quiera un recurso extra que no
ha pedido pero que debería tener de todas formas, puede enviar una trama
`PUSH_PROMISE` (sobre el flujo de petición) mostrando cómo es la petición a la
que el push es una respuesta, y luego enviar esa respuesta real sobre un nuevo
flujo.

Aunque el cliente haya dicho que los envíos son aceptables de antemano, cada
flujo individual enviado puede ser cancelado en cualquier momento si el cliente
lo considera conveniente. Entonces envía una trama `CANCEL_PUSH` al servidor.

## Problemática

Desde que esta característica se discutió por primera vez en el desarrollo de
HTTP/2 y más tarde después de que el protocolo se enviara y se desplegara en
Internet, esta característica se ha discutido, no ha gustado y se ha machacado
de innumerables maneras diferentes con el fin de conseguir que sea útil.

El push nunca es "gratuito", ya que, aunque ahorra medio viaje de ida y
vuelta, sigue utilizando ancho de banda. A menudo es difícil o imposible para
el servidor saber con un alto nivel de certeza si un recurso debe ser enviado 
por push o no.
