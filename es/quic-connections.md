# Conexiones

Una conexión QUIC es una conversación única entre dos end-points QUIC. El
establecimiento de la conexión de QUIC combina la negociación de la versión con
los handshakes criptográficos y de transporte para reducir la latencia del 
establecimiento de la conexión.

Para enviar realmente datos a través de una conexión de este tipo, hay que crear
y utilizar uno o más flujos.

## Identificación de la conexión

Cada conexión posee un conjunto de identificadores de conexión, o IDs de
conexión, cada uno de los cuales puede ser utilizado para identificar la
conexión. Los IDs de conexión son seleccionados de forma independiente por los 
end-points; cada punto final selecciona los IDs de conexión que utiliza su 
compañero.

La función principal de estos IDs de conexión es asegurar que los cambios en el
direccionamiento en las capas inferiores del protocolo (UDP, IP, y por debajo)
no causen que los paquetes de una conexión QUIC sean entregados al end-point 
equivocado.

Aprovechando el ID de conexión, las conexiones pueden migrar entre direcciones 
IP e interfaces de red de una manera que TCP nunca podría. Por ejemplo, la 
migración permite que una descarga en curso pase de una conexión de red celular
a una conexión wifi más rápida cuando el usuario traslada su dispositivo a un
lugar que ofrece wifi. Del mismo modo, la descarga puede continuar a través de
la conexión celular si el wifi no está disponible.

## Números de puerto

QUIC está construido sobre UDP, por lo que se utiliza un campo de número de
puerto de 16 bits para diferenciar las conexiones entrantes.

## Negociación de la versión

Una petición de conexión QUIC originada por un cliente le dirá al servidor qué
versión del protocolo QUIC quiere hablar, y el servidor responderá con una lista
de versiones soportadas para que el cliente las seleccione.
