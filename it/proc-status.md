# Status

Il gruppo di lavoro QUIC ha lavorato alacremente a partire dal tardo 2016
ad una specifica di protocollo e la sua volontà è di completare tale sforzo
entro Luglio 2019.

A Novembre 2018, ancora non abbiamo notizia di test di interoperabilità
estesi su HTTP/3 - solo fra le due implementazioni esistenti che tuttavia
non sono guidate da un browser ne da un software opensource lato server.

Esistono all'incirca quindici [Implementazioni di QUIC
](https://github.com/curl/curl/wiki/QUIC-implementation) nella lista wiki
del gruppo di lavoro, ma ovviamente non tutte possono operare allo stesso
livello dell'ultima bozza delle specifiche.

Implementare QUIC non è affatto semplice, dato che è in continua evoluzione
anche quando sembra stabilizzatosi.

## Servers

Non vi è alcun comunicato pubblico rispetto al supporto di QUIC in Apache o
nginx.

## Clients

Nessun editore di browser ha rilasciato qualsivoglia versione -nemmeno in
beta- che sia in grado di utilizzare la versione IETF di QUIC o HTTP/3.

Google Chrome contiene la sua propria implementazione di QUIC in salsa Google
da svariati anni; tale versione Google non è compatibile con le bozze IETF
e l'implementazione di HTTP differisce dalla versione HTTP/3 ufficiale.

## Ostacoli all'implementazione

QUIC ha deciso di utilizzare TLS 1.3 come fondazione per gli strati di
sicurezza e di crittografia al fine di evitare di dover reinventare la ruota,
e poter contare su standard "forti", ad alta credibilità. Tuttavia nel fare
ciò il gruppo di lavoro ha infine riadattato l'utilizzo del protocollo TLS
con QUIC, utilizzando solamente "messaggi TLS" e mai "records TLS".

Quello che potrebbe sembrare una innocente modifica, in realtà ha causato
non pochi grattacapi a chi era in procinto di implementare uno stack QUIC.
Le librerie TLS esistenti con supporto a TLS 1.3 non dispongono di un numero
sufficiente di API per esporre tale funzionalità e permettere quindi a QUIC
di accedervi. Se è vero che molti degli sviluppatori/implementatori di QUIC
appartengono a grandi organizzazioni che in parallelo sviluppano il proprio
stack TLS, ciò non è esattamente vero per tutti.

Ad esemnpio OpenSSL -leader in campo opensource- non fornisce alcuna API per
controllare tale funzione ed non ha espresso alcuna volontà di sviluppare
un tale componente (almeno fino a Novembre 2018).

Questa situazione porterà ad incontrare ostacoli nella messa in campo della
tecnologia QUIC, visto che i differenti stack dovranno basarsi su librerie
TLS proprie o di terze parti, utilizzare versioni di OpenSSL modificate o
necessitare di aggiornamenti varii.

## Kernel e carico sulla CPU

Google e Facebook hanno entrambi affermato che le loro installazioni QUIC su
larga scala consumano circa il doppio della CPU per servire la stessa quantità
di contenuti rispetto ad una più classica connessione HTTP/2 su TLS e TCP.

Spiegazioni plausibili a questo fenomeno includono:

- il fatto che la parte UDP nel kernel Linux non sia altrettanto ottimizzata
  quanto lo stack TCP, dato che UDP non era finora mai stato utilizzato per
  trasferimenti ad altissima velocità come questi

- il fatto che per QUIC non esistano dispositivi di accelerazione hardware e
  offloading come invece è il caso per TCP e TLS. Notiamo rarissime eccezioni
  per dispositivi dedicati ad UDP.

Non vi sono ragioni per non essere convinti che le performance aumenteranno
ed i requisiti CPU si abbasseranno nel tempo.
