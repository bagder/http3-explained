# URLs HTTPS://

HTTP/3 si servirà di URLs del tipo `HTTPS://`. Il mondo è pieno di questo
tipo di URL ed è stato osservato che sarebbe impraticabile ed illogico
proporre un ulteriore schema di URL per il nuovo protocollo. Similmente a
come HTTP/2 non avesse bisogno di un nuovo schema, cosi fu per HTTP/3.

La complessità aggiunta da HTTP/3 è evidente se guardiamo al fatto che
HTTP/2 -seppur rivoluzionario nel trasporto di HTTP a livello di trama- era
ancora basato su TLS e TCP come nel caso del predecessore HTTP/1. Il fatto
che HTTP/3 lavori su QUIC fa vacillare un certo numero di assunzioni.

Il caro vecchio URL "clear-text" `HTTP://` verrà lasciato intatto e sarà
via via abbandonato nel momento in cui si passerà a modalità di trasporto
più sicure. Richieste verso questo tipo di URL non riceveranno alcun
upgrade a HTTP/3. Nella realtà dei fatti, ben poche di queste connessioni
ricevono upgrade a HTTP/2, ma per altri motivi.

## Connessione iniziale

La prima connessione ad una risorsa o host non ancora visitato via URL
HTTPS:// sarà probabilmente stabilita via TCP (eventualmente in parallelo
con un tentativo di connessione QUIC). L'host distante potrebbe essere un
vecchio server che non fornisce supporto a QUIC, o potrebero esservi
dispositivi sul percorso di rete che impediscono il successo della connessione
via QUIC.

Un client moderno negozierebbe probabilment HTTP/2 in prima istanza. Una
volta che tale connessione fosse stata effettuata, e che il server avesse
risposto ad una richiesta HTTP, il server potrebbe comunicare al client la
disponibilità del supporto e la preferenza per HTTP/3.
