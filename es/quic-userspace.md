## Espacio de usuario

Implementar un protocolo de transporte en el espacio de usuario ayuda a permitir
una rápida iteración del protocolo, ya que es comparativamente fácil evolucionar
el protocolo sin necesidad de que los clientes y servidores actualicen el núcleo
de su sistema operativo para desplegar nuevas versiones.

Nada inherente a QUIC impide que sea implementado y ofrecido por los kernels de
los sistemas operativos en el futuro, si a alguien le parece una buena idea.

### Muchas implementaciones

Un efecto obvio de implementar un nuevo protocolo de transporte en el espacio de
usuario es que podemos esperar ver muchas implementaciones independientes. 

Es probable que diferentes aplicaciones incluyan (o se superpongan) diferentes
implementaciones de HTTP/3 y QUIC en un futuro previsible.
