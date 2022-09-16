# URLs HTTPS://

HTTP/3 se realizará utilizando URLs `HTTPS://`. El mundo está lleno de estas
URLs y se ha considerado poco práctico y francamente irrazonable introducir
otro esquema de URL para el nuevo protocolo. Al igual que HTTP/2 no necesitaba
un nuevo esquema, tampoco lo necesitará HTTP/3.

La complejidad añadida en la situación de HTTP/3 es, sin embargo, que mientras
HTTP/2 era una forma completamente nueva de transportar HTTP a través del
cable, seguía basándose en TLS y TCP como lo hacía HTTP/1. El hecho de que
HTTP/3 se realice sobre QUIC cambia las cosas en algunos aspectos importantes.

Las URLs heredadas, de texto claro, `HTTP://` se dejarán como están y, a medida
que avancemos hacia un futuro con transferencias más seguras, probablemente se
utilizarán cada vez con menos frecuencia. Las peticiones a estas URLs
simplemente no se actualizarán para utilizar HTTP/3. En realidad tampoco se
actualizan a HTTP/2, pero por otras razones.

## Conexión inicial

La primera conexión a un host nuevo, no visitado previamente, para una URL
HTTPS:// probablemente tenga que hacerse sobre TCP (posiblemente además de un
intento paralelo de conexión vía QUIC). El host puede ser un servidor heredado
sin soporte para QUIC o puede haber una caja intermedia que ponga obstáculos
que impidan el éxito de una conexión QUIC.

Un cliente y un servidor modernos presumiblemente negociarían HTTP/2 en el
primer apretón de manos. Cuando la conexión se haya establecido y el servidor
responda a una petición HTTP del cliente, el servidor puede informar al cliente
sobre su soporte y preferencia por HTTP/3.
