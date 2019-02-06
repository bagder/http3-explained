# Connessioni

Una connessione QUIC è una conversazione singola fra due end-points QUIC.
La modalità di inizializzazione della connessione QUIC combina la negoziazione
della versione con le negoziazioni dell'algoritmo crittografico e del trasporto
al fine di ridurre la latenza di setup della connessione.

Per essere in grado di inviare dati attraverso tale connessione, uno o più
flussi devono essere istanziati ed utilizzati.

## ID della connessione

Ogni connessione dispone di un insieme di identificatori di connessione,
ognuno dei quali può essere utilizzato per identificare la connessione stessa.
Gli ID sono selezionati indipendentemente da ognuna delle estremità; ogni
endpoint assegna un ID alla connessione con il suo corrispondente.

La funzione primaria dell'ID di connessione è di assicurare che i cambiamenti
nell'indirizzamento dei protocolli di livello inferiore (UDP, IP ed oltre) non
provochino malfunzionamenti nella consegna dei pacchetti su connessioni QUIC
ad esempio consegnandoli dal lato sbagliato.

Traendo vantaggio dall'ID di connessione, le connessioni possono dunque essere
migrate attraverso indirizzi IP ed interfacce, in modi mai previsti dal TCP.
Per esempio, si potrà migrare una connessione di download in corso su una rete
mobile verso una connessione wifi a banda larga, senza interrompere il download.
In modo analogo, il download potrà procedere su rete mobile se la connessione
wifi dovesse interrompersi.

## Numeri di porta

Essendo QUIC costruito su UDP, un campo a 16bit è utilizzato per distinguere
le connessioni in ingresso.

## Negoziazione delle versioni

Una connessione QUIC originata da un client renderà noto al server quale
versione QUIC esso preferisca parlare, ed il server risponderà con una lista
delle versioni supportate, lasciando la scelta finale al client.
