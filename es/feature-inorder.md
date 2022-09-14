## Entrega en orden

QUIC garantiza la entrega en orden de los flujos, pero no entre flujos. Esto
significa que cada flujo enviará datos y mantendrá el orden de los mismos, ¡pero
cada flujo puede llegar al destino en un orden diferente al que la aplicación lo
envió!

Por ejemplo: los flujos A y B son transferidos desde un servidor a un cliente.
El flujo A se inicia primero y luego el flujo B. En QUIC, un paquete perdido 
sólo afecta al flujo al que pertenece el paquete perdido. Si el flujo A pierde
un paquete pero el flujo B no, el flujo B puede continuar sus transferencias y
completarlas mientras el paquete perdido del flujo A es retransmitido. Esto no
era posible con HTTP/2.

Ilustrado aquí con un flujo amarillo y otro azul enviados entre dos end-points
de QUIC a través de una única conexión. Son independientes y pueden llegar en un
orden diferente, pero cada flujo se entrega de forma fiable a la aplicación en
orden.

![Dos flujos QUIC entre dos ordenadores](../images/quic-chain-streams.png)
