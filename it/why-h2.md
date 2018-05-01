## Ricordate HTTP/2 ?

La specifica HTTP/2 [RFC 7540](http://httpwg.org/specs/rfc7540.html) è stata
pubblicata nel Maggio 2015 e da allora il protocollo è stato implementato e 
largamente distribuito attraverso l'intero Internet e il world wide web.

Ad inizio 2018, quasi il 40% dei top-1000 siti web funziona in HTTP/2, circa
il 70% di tutte le richieste HTTPS che Firefox invia riceve risposte di tipo
HTTP/2, e tutti i principali server, proxy e browser lo supportano.

HTTP/2 cerca di risolvere limiti intrinsechi ad HTTP/1; con l'introduzione di
tale seconda versione di HTTP gli utenti non necessitano più di svariati work-
around precedentemente impiegati. Alcuni di essi caricano gli sviluppatori di
responsabilità aggiuntive, non previste.

Una delle prime funzioni di HTTP/2 è il multiplexing, tecnica che permette di
spedire flussi logici multipli all'interno della stessa connessione TCP, Ciò
permette di rendere tutto più rapido e fluido. Fa si che il controllo di flusso
sia applicato in maniera più efficace, permette agli utenti di utilizzare il
TCP a fondo, di saturare la banda, di rendere le connessioni TCP più durature
- il che permette di raggiungere la velocità massima nella maggior parte dei
casi. La compressione degli header permette di utilizzare meno banda.

Con HTTP/2, I browser usano tipicamente *una* connessione TCP per ogni host,
piuttosto che le precedenti *6*. Difatti tecniche come il "desharding" e la
condensazione delle connessioni proprie di HTTP/2 potrebbero ridurre ancora 
e ancora il numero di connessioni totali.

In HTTP/2 il problema del "bloccaggio di inizio fila" è stato risolto. In 
breve, il client era costretto ad aspettare la fine dell'elaborazione della 
richiesta in corso prima di poter prendere in carico la risposta alla domanda
in attesa.

![http2 man](../images/h2-man.jpg)
