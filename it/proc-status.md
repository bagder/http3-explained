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

Il supporto per QUIC e HTTP/3 in NGINX è in fase di sviluppo.
Il rilascio delle nuove funzionalità è previsto durante
[il ciclo di sviluppo di NGINX 1.17](https://trac.nginx.org/nginx/milestone/nginx-1.17).

Non vi è alcun comunicato pubblico rispetto al supporto di QUIC in Apache.

## Clients

Nessun produttore di web-browser ha rilasciato una versione che sia in grado
di utilizzare la versione IETF di QUIC o HTTP/3.

Google Chrome contiene la sua propria implementazione di QUIC in salsa Google
da svariati anni; tale versione Google non è compatibile con le bozze IETF
e l'implementazione di HTTP differisce dalla versione HTTP/3 ufficiale.

Mozilla sta sviluppando [Neqo](https://github.com/mozilla/neqo/) -
un'implementazione di QUIC e HTTP/3 scritta in [Rust](https://www.rust-lang.org/).
Neqo [sarà integrato](https://github.com/mozilla/neqo/issues/10)
in [Necko](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Necko)
(una libreria di rete usata in molte applicazioni di Mozilla - incluso Firefox).

curl ha rilasciato un primo supporto sperimentale per HTTP/3 (draft-22) con 
la release 7.66.0 dell' 11 Settembre 2019. Per l'implementazione di HTTP/3,
curl può usare sia la libreria Quiche di
Cloudflare che la famiglia di librerie ngtcp2.

## Ostacoli all'implementazione

Per non dover re-inventare la ruota e poter contare su standard affermati,
QUIC ha deciso di utilizzare TLS 1.3
come fondazione per gli strati di sicurezza e di crittografia. Tuttavia, nel fare
ciò, il gruppo di lavoro ha infine riadattato l'utilizzo del protocollo TLS
con QUIC, utilizzando solamente "messaggi TLS" e mai "records TLS".

Quello che potrebbe sembrare un'innocente modifica, in realtà ha causato
non pochi grattacapi a chi era in procinto di implementare uno stack QUIC.
Le librerie TLS esistenti con supporto a TLS 1.3 non dispongono di un numero
sufficiente di API per esporre tale funzionalità e permettere quindi a QUIC
di accedervi. Se è vero che molti degli sviluppatori/implementatori di QUIC
appartengono a grandi organizzazioni che in parallelo sviluppano il proprio
stack TLS, ciò non è esattamente vero per tutti.

Ad esempio OpenSSL -leader in campo opensource- non fornisce alcuna API per
controllare tale funzione.
Il piano per risolvere questo problema è delineato nella [PR
8797](https://github.com/openssl/openssl/pull/8797), che punta ad introdurre
delle API simili a quelle di BoringSSL.

Questa situazione porterà ad incontrare ostacoli nella messa in campo della
tecnologia QUIC, visto che i differenti stack dovranno basarsi su librerie
TLS proprie o di terze parti, utilizzare versioni di OpenSSL modificate o
necessitare di aggiornamenti vari.

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
