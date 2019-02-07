## Ricordate HTTP/2 ?

La specifica HTTP/2 [RFC 7540](https://httpwg.org/specs/rfc7540.html) è stata
pubblicata nel Maggio 2015 e da allora il protocollo è stato implementato e
largamente distribuito attraverso l'intero Internet e il world wide web.

Ad inizio 2018, quasi il 40% dei top-1000 siti web funziona in HTTP/2: circa il
70% di tutte le richieste HTTPS inviate da Firefox ha ricevuto risposte di tipo
HTTP/2. Tutti i principali server, proxy e browser supportano h2.

HTTP/2 cerca di risolvere svariati limiti intrinsechi ad HTTP/1; con
l'introduzione di tale seconda versione di HTTP gli utenti non sono più
obbligati ad utilizzare work-around e gabole complicate. Tali sotterfugi 
caricano inutilmente gli sviluppatori di responsabilità non previste.

Una delle funzioni principali in HTTP/2 è il multiplexing, tecnica che
permette di inviare molteplici flussi logici (indipendenti) all'interno di una
stessa connessione TCP. Ciò rendre il tutto più rapido e fluido. Fa si che il
controllo di flusso sia applicato in maniera più efficace, permette agli utenti
di sfruttare il TCP appieno, di saturare la banda, di rendere le connessioni
TCP più durature -il che permette nella maggior parte dei casi di raggiungere
la massima velocità. La compressione degli header permette di risparmiare banda.

Con HTTP/2, i browser usano tipicamente *una* connessione TCP per ogni host
rispetto alle precedenti *sei*. In effetti, tecniche come il "desharding" e la
condensazione ("coalescing") delle connessioni HTTP/2 potrebbero ridurre
ulteriormente il numero di connessioni totali.

HTTP/2 risolve il problema del "bloccaggio di inizio fila": il client era
costretto ad aspettare la fine dell'elaborazione della richiesta in corso prima
di poter prendere in carico la risposta alla domanda in attesa. Ora non più.

![http2 man](../images/h2-man.jpg)
