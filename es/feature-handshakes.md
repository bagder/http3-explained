# Rápido establecimiento de comunicación

QUIC ofrece configuraciones de conexión 0-RTT y 1-RTT, lo que significa que, en 
el mejor de los casos, QUIC no necesita ningún viaje de ida y vuelta adicional
al establecer una nueva conexión. El más rápido de los dos, el handshake 0-RTT,
sólo funciona si se ha establecido una conexión previa con un host y se ha 
almacenado en caché un secreto de esa conexión.

## Datos tempranos

QUIC permite a un cliente incluir datos ya en el handshake 0-RTT. Esta
característica permite a un cliente entregar datos al peer tan rápido como sea
posible, y eso entonces, por supuesto, permite al servidor responder y enviar 
datos de vuelta incluso antes.
