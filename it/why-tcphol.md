## Bloccaggio ad inizio della coda TCP

HTTP/2 è comunque ancora basato su TCP seppur utilizzi un minor numero di
connessioni rispetto ai predecessori. Il TCP è un protocollo di trasferimento
affidabile; lo si può immaginare come una corda immaginaria tesa fra due host.
Ciò che viene appeso ad un estremo, arriverà all'altro, nello stesso ordine -
a costo dell'interruzione della connessione.

In HTTP/2 il browser avrà la tendenza a soddisfare decine o anche centinaia di
trasferimenti attraverso la stessa connessione TCP.

Se un singolo pacchetto venisse perso, abbandonato o scartato da qualche parte 
sulla rete, fra due endopoints che stessero dialogando in HTTP/2, tale dialogo
verrebbe sospeso fino alla ri-trasmissione e all'arrivo di tale pacchetto a 
destinazione. Date che il TCP è raffigurato da questa "corda", tutto ciò (tutti
i dati) che segue (seguono) il pacchetto in sospeso dovrà (dovranno) attendere.

Si parla quindi di bloccaggio ad inizio della coda, basato su TCP!

Se il tasso di perdita di pacchetti dovesse incrementare, HTTP/2 subirebbe un
degrado di prestazioni. A 2% di perdita di pacchetti (che comunque rappresenta
una qualità infima) svariati test hanno dimostrato che gli utenti di HTTP/1 
ottengono risultati di gran lunga migliori, visto che un tasso di perdita del
2% distribuito su sei connessioni ha meno influenza che su una sola, 
permettendo così che certe connessioni continuino senza essere influenzate.

Porre rimedio a tale situazione non sarà semplice -se non impossibile- se si
continua ad usare il TCP..

