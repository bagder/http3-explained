# Osificación

Internet es una red de redes. Hay equipos instalados en Internet en muchos 
lugares diferentes a lo largo del camino para asegurarse de que esta red de 
redes funciona como se supone que debe hacerlo. Estos dispositivos, las cajas 
que están distribuidas en la red, son lo que a veces llamamos cajas intermedias.
Cajas que se sitúan en algún lugar entre los dos puntos finales que son las 
partes principales implicadas en una transferencia de datos de red tradicional. 

Estas cajas sirven para muchos propósitos específicos diferentes, pero creo que
podemos decir que universalmente se ponen ahí porque alguien piensa que deben 
estar ahí para que las cosas funcionen.

Las cajas intermedias enrutan los paquetes IP entre las redes, bloquean el 
tráfico malicioso, hacen NAT (traducción de direcciones de red), mejoran el 
rendimiento, algunas intentan espiar el tráfico que pasa y mucho más.

Para desempeñar sus funciones, estas cajas deben conocer las redes y los 
protocolos que supervisan o modifican. Para ello ejecutan un software. Un 
software que no siempre se actualiza con frecuencia.

Aunque son componentes de pegamento que mantienen unida a Internet, a menudo no 
se mantienen al día con la última tecnología. El centro de la red no suele 
moverse tan rápido como los bordes, como los clientes y los servidores del 
mundo.

Los protocolos de red que estas cajas podrían querer inspeccionar, y tener ideas
sobre lo que está bien y lo que no, tienen entonces este problema: estas cajas 
se desplegaron hace algún tiempo cuando los protocolos tenían un conjunto de 
características de esa época. Al introducir nuevas características o cambios en 
el comportamiento que no se conocían antes, se corre el riesgo de que dichas 
cajas lo consideren malo o ilegal. Es muy posible que ese tráfico se elimine o 
se retrase hasta el punto de que los usuarios no quieran utilizar esas 
funciones.

Esto se llama "osificación del protocolo".

Los cambios en TCP también sufren de osificación: algunas cajas entre un cliente
y el servidor remoto detectarán nuevas opciones TCP desconocidas y bloquearán 
dichas conexiones ya que no saben cuáles son las opciones. Si se permite 
detectar los detalles del protocolo, los sistemas aprenden cómo se comportan 
normalmente los protocolos y con el tiempo resulta imposible cambiarlos.

La única forma realmente eficaz de "combatir" la osificación es cifrar la mayor 
parte posible de la comunicación para evitar que las cajas intermedias vean gran
parte del protocolo que pasa.
