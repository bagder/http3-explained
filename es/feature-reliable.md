## Transferencias de datos fiables

Aunque UDP no es un transporte fiable, QUIC añade una capa sobre UDP que que
introduce la fiabilidad. Ofrece retransmisiones de paquetes, control de 
congestión control de la congestión, ritmo y otras características presentes en
TCP.

Los datos enviados a través de QUIC desde un end-point aparecerán en el otro
extremo tarde o temprano, siempre que se mantenga la conexión.
