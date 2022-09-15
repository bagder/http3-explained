# 0-RTT

Para reducir el tiempo necesario para establecer una nueva conexión, un cliente
que se ha conectado previamente a un servidor puede almacenar en caché ciertos
parámetros de esa conexión y posteriormente establecer una conexión **0-RTT**
con el servidor. Esto permite al cliente enviar datos inmediatamente sin esperar
a que se complete el handshake.
