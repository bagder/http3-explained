## Bloccaggio ad inizio della coda TCP

HTTP/2 è comunque ancora basato su TCP seppur utilizzi un minor numero di
connessioni rispetto ai predecessori. Il TCP è un protocollo di trasferimento
affidabile; lo si può immaginare come una corda immaginaria tesa fra due host.
Ciò che viene appeso ad un estremo arriverà all'altro, nello stesso ordine -
a costo dell'interruzione della connessione.

![a TCP chain between two computers](../images/tcp-chain.png)

Con HTTP/2, il browser avrà la tendenza a soddisfare decine o anche centinaia
di trasferimenti attraverso la stessa connessione TCP.

Se un singolo pacchetto venisse perso, abbandonato o scartato da qualche
parte sulla rete, fra due endopoints che stessero dialogando in HTTP/2, tale
dialogo verrebbe sospeso fino alla ri-trasmissione e all'arrivo di tale
pacchetto a destinazione. Osservando la catena con cui è raffigurato il TCP,
capiamo come -in caso di interruzione del link- tutti i dati che seguono il
pacchetto in sospeso dovranno attendere.

Una illustrazione della metafora della catena nel momento in cui due flussi
siano trasmessi sulla medesima connessione. Un flusso in rosso, uno in giallo:

![the chain showing links in different colors](../images/tcp-chain-streams.png)

Si parla quindi di bloccaggio ad inizio della coda, basato su TCP!

Se il tasso di perdita di pacchetti dovesse incrementare, HTTP/2 subirebbe un
degrado di prestazioni. A 2% di perdita di pacchetti (che comunque rappresenta
una qualità infima) svariati test hanno dimostrato come gli utenti di HTTP/1
ottengano risultati di gran lunga migliori, stimando che un tasso di perdita
del 2% distribuito su sei connessioni abbia meno influenza che su una sola,
permettendo così alle rimanenti connessioni di proseguire senza intralcio.

Porre rimedio a tale empasse non sarà semplice -se non impossibile- finché si
continuerà ad usare il TCP..

## L'impiego di flussi indipendenti evita il blocco

QUIC è composto da una fase di setup della connessione fra i due estremi, fase
che rende la connessione sicura e la consegna dei dati affidabile.

![una catena QUIC fra due computers](../images/tcp-chain.png)

Seppur instradati su una stessa connessione, i due flussi sono trattati in
maniera indipendente tanto che se uno dei due collegamenti fosse interrotto,
solo il flusso in questione sarà obbligato ad attendere la ri-trasmissione
della risorsa perduta, senza alcun impatto sull'altro flusso parallelo.

Qui di seguito illustrati i due flussi (streams) scambiati dai due end-ponts,
uno in blu ed uno in giallo.

![due flussi QUIC fra due computers](../images/quic-chain-streams.png)
