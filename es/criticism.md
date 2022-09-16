# Crítica

## UDP nunca funcionará

Muchas empresas, operadores y organizaciones bloquean o limitan el tráfico UDP
fuera del puerto 53 (utilizado para DNS) ya que en los últimos días se ha
abusado de él para realizar ataques. En particular, algunos de los protocolos
UDP existentes y las implementaciones de servidores populares para ellos han
sido vulnerables a los ataques de amplificación en los que un atacante puede
hacer una gran cantidad de tráfico saliente para atacar a víctimas inocentes.

QUIC tiene una mitigación incorporada contra los ataques de amplificación al
requerir que el paquete inicial sea de al menos 1200 bytes y mediante una
restricción en el protocolo que dice que un servidor no debe enviar más de tres
veces el tamaño de la solicitud en respuesta sin recibir un paquete del cliente
en respuesta.

## UDP es lento en los núcleos

Esto parece ser la verdad, al menos inicialmente. Por supuesto, no podemos saber
cómo evolucionará esto y cuánto de esto es simplemente el resultado de que el
rendimiento de la transferencia UDP no ha estado en el foco de los
desarrolladores durante muchos años.

Para la mayoría de los clientes, es probable que esta "lentitud" ni siquiera se
note.

## QUIC consume demasiada CPU

Al igual que la observación anterior de que "UDP es lento", esto se debe en
parte a que el uso de TCP y TLS en el mundo ha tenido más tiempo para madurar,
mejorar y obtener asistencia de hardware.

Hay razones para esperar que esto mejore con el tiempo, y ya [estamos viendo
algunas mejoras en este espacio]
(https://www.fastly.com/blog/measuring-quic-vs-tcp-computational-efficiency).
La cuestión es hasta qué punto este uso adicional de la CPU perjudicará a los
implantadores.

## Esto es sólo Google

No, no lo es. Google llevó la especificación inicial al IETF después de haber
demostrado, a gran escala en Internet, que el despliegue de este estilo de
protocolo sobre UDP realmente funciona y tiene un buen rendimiento.

Desde entonces, personas de un gran número de empresas y organizaciones han
trabajado en la organización neutral de proveedores IETF para elaborar un
protocolo de transporte estándar a partir de él. En ese trabajo, los empleados
de Google han participado, por supuesto, pero también lo han hecho los
empleados de un gran número de otras empresas que están interesadas en promover
el estado de los protocolos de transporte en Internet, como Mozilla, Fastly,
Cloudflare, Akamai, Microsoft, Facebook y Apple.

## Es una mejora demasiado pequeña

Esto no es realmente una crítica, sino una opinión. Tal vez lo sea, y tal vez
sea una mejora demasiado pequeña desde que se lanzó HTTP/2.

Es probable que HTTP/3 funcione mucho mejor en redes con pérdida de paquetes,
ofrece handshakes más rápidos, por lo que mejorará la latencia tanto percibida
como real. Pero, ¿es esto suficiente para motivar a la gente a desplegar el
soporte de HTTP/3 en sus servidores y servicios? El tiempo y las futuras
mediciones de rendimiento seguramente lo dirán.
