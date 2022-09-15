# Spin Bit

Una de las discusiones de diseño quizás más largas dentro del grupo de trabajo
de QUIC que ha sido objeto de varios cientos de correos y horas de discusiones 
se refiere a un solo bit: el Spin Bit.

Los defensores de este bit insisten en la necesidad de que los operadores y las
personas que se encuentran en la ruta entre dos puntos finales de QUIC puedan
medir la latencia.

A los que se oponen a esta característica no les gusta la posible fuga de 
información.

## Girando un poco

Ambos end-points, el cliente y el servidor, mantienen un valor de giro, 0 o 1,
para cada conexión QUIC, y establecen el spin bit en los paquetes que envían
para esa conexión al valor apropiado.

A continuación, ambos lados envían paquetes con ese bit de giro fijado al mismo
valor durante el tiempo que dura un viaje de ida y vuelta y luego se alterna el
valor. El efecto es entonces un pulso de unos y ceros en ese campo de bits que
los observadores pueden monitorizar.

Esta medición sólo funciona cuando el emisor no está limitado por la aplicación
ni por el control de flujo, y la reordenación de los paquetes en la red también
puede hacer que los datos sean ruidosos.
