# Negoziazioni veloci

QUIC offre entrambi i metodi di connessione 0-RTT e 1-RTT, nel senso che nel
migliore dei casi QUIC non ha bisogno di round-trips aggiuntivi per iniziare
una nuova connessione. Il più veloce dei due metodi, la negoziazione a 0-RTT,
funziona solo se vi è gia stata una connessione fra i due host in question e
solo se il "segreto" per tale connessione è stato aggiunto alla cache.

## Dati in anticipo

QUIC permette ai client di aggiungere dati gia a partire dalla fase di
negoziazione a 0-RTT. Questa caratteristica permette ad un client di spedire
dati al proprio interlocutore il più veloce possibile; ciò permette al
server di rispondere aggiungendo altri dati ancora più velocemente.
