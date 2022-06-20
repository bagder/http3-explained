# Prioritizzazione in HTTP/3

Uno dei frame facenti parte di ogni flusso HTTP/3 è il campo `PRIORITY`.
È usato per segnalare la priorità e l'ordine di dipendenza fra flussi
diversi molto similmente a quanto gia avveniva in HTTP/2.

Il frame può essere impostato in modo che un flusso dipenda da un altro e
può definire un "peso specifico" su ogni determinato flusso.

Un flusso dipendente avrà diritto ad allocare risorse solamente se tutti
gli altri flussi dai quali esso dipende fossero gia in fase di chiusura,
o non fosse possibile avanzare ulteriormente su tali suddetti flussi.

Uno stream assume un valore compreso fra 1 e 256. La regola vuole che
un flusso con uno stesso antenato **dovrebbe** allocare risorse in maniera
proporzionale basandosi sul peso specifico di ognuna.
