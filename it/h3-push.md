# HTTP/3 Server push

La modalita "server push" di HTTP/3 è tutto sommato simile a quanto
descritto per HTTP/2 nella ([RFC 7540
](https://httpwg.org/specs/rfc7540.html)) pur usando meccanismi diversi.

Una "server push" è a tutti gli effetti la risposta ad una richiesta che il
client in realtà non ha mai inviato !

Le "server push" sono difatti autorizzate solamente in caso il client abbia
deciso di accettarle. In HTTP/3 il client imposta addirittura un limite al
numero massimo di risposte push che è disposto ad accettare, comunicando al
server l'ID di fluso più alto che sarà disposto a trattare. Se il server
dovesse tentare di inviare flussi al di sopra dell'ID indicato, ciò
provocherebbe un errore di connessione.

Se il server dovesse pensare che il client possa aver bisogno di una
determinata risorsa -risorsa comunque ritenuta necessaria- potrebbe volergli
inviare un frame detto `PUSH_PROMISE` (all'interno dello stesso flusso della
richiesta) contenente le coordinate della richiesta per la risorsa in
questione ed in seguito inviare la risposta all'interno di un nuovo flusso. 

Anche nel momento in cui le "server push" dovessero essere ritenute credibili
da parte del client, ognuna delle singole "push" può essere annullata ad ogni
momento se il client dovesse in qualche modo ritenerlo necessario. In tal
caso invierebbe un frame `CANCEL_PUSH` al server.

## Problematiche

Questa caratteristica è stata messa in discussione, criticata e rigirata sin
dal primo momento, sia durante lo sviluppo di HTTP/2 sia dopo la sua
pubblicazione e impiego su larga scala, tentando di renderla utilizzabile.

Un invio in "push" non è mai gratis, benché utilizzi solo metà del tempo di
round-trip, occupa banda passante. È spesso difficile -impossibile- dal
punto di vista del server stabilire con certezza se una determinata risorsa
possa necessitare (beneficiare) del "push" o meno.
