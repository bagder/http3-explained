## Flussi multipli all'interno di una stessa connessione

Similmente a SCTP, SSH e HTTP/2, QUIC sfrutta flussi logicamente separati
all'interno di una stessa connessione fisica. Un numero di stream paralleli
può trasferire simultaneamente dati sulla stessa connessione senza influenzare
gli altri flussi concorrenti.

Una connessione viene negoziata e messa in opera fra due punti remoti, in modo
similare a quanto avviene per TCP. Una connessione QUIC è stabilita verso una
porta e un indirizzo IP, tuttavia una volta stabilita la connessione viene
identificata da un ID detto "ID di connessione".

All'interno di una connessione gia stabilita, ognuno dei due estremi può
creare un flusso e spedire dei dati all'altro estremo. Un singolo flusso
viene consegnato "in ordine" ed è ritenuto affifabile, mentre altri flussi
paralleli potrebbero eventualmente essere ricevuti "fuori ordine".

QUIC offre un controllo di flusso a livello di connessione e di flusso.

Maggiori dettagli nelle sezioni [connessioni](quic-connections.md) e
[streams](quic-streams.md).
