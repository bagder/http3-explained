## La experiencia de HTTP/2

La especificación RFC 7540 de HTTP/2 fue publicada en mayo de 2015, justo un mes
antes que QUIC fuera llevado a la IETF por primera vez.

Con HTTP/2, se sentaron las bases para cambiar HTTP sobre la red y el grupo de 
trabajo que creó HTTP/2 ya tenía la idea de que esto ayudaría a iterar a nuevas
versiones de HTTP mucho más rápido de lo que se había tardado en pasar a la 
versión 2 desde la versión 1 (unos 16 años).

Con HTTP/2, los usuarios y los stack de software se acostumbraron a la idea de
que HTTP ya no puede suponerse un protocolo basado en texto de forma serial.

HTTP-over-QUIC (HTTP/3) se basa en HTTP/2 y sigue muchos de los mismos conceptos
pero traslada algunos de los aspectos específicos de la capa HTTP, ya que están
cubiertos por QUIC.
