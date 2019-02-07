## User-space (spazio-utente)

Implementare un protocollo di trasporto all'interno dello user-space
permette di poter manipolare/programmare il protocollo facilmente,
senza necessita di aggiornare il kernel o il sistema operativo ad ogni
evoluzione delle librerie client/server.

Non vi sono tuttavia ostacoli fattuali alla implementazione di QUIC
all'interno del kernel; qualcuno in futuro se ne occuperà, se veramente
ve ne sarà la necessità.

### Molte implementazioni

L'implementazione di un nuovo protocollo di trasporto all'interno dello
user-space ha per effetto la nascita di molteplici implementazioni.

In un futuro prossimo, è certo che le diverse applicazioni conterranno
(o si baseranno) su implementazioni eterogenee di HTTP/3 e QUIC.
