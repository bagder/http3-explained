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

QUIC decided to use TLS 1.3 as the foundation for the crypto and security
layer to avoid inventing something new and instead lean on a trustworthy and
existing protocol. However, while doing this, the working group also decided
that to really streamline the use of TLS in QUIC, it should only use "TLS
messages" and not "TLS records" for the protocol.

This might sound like an innocuous change, but this has actually caused a
significant hurdle for many QUIC stack implementors. Existing TLS libraries
that support TLS 1.3 simply do not have APIs enough to expose this
functionality and allow QUIC to access it. While several QUIC implementors
come from larger organizations who work on their own TLS stack in parallel,
this is not true for everyone.

The dominant open source heavyweight OpenSSL for example, does not have any
API for this and has not expressed any desire to provide any such anytime soon
(as of November 2018).

This will eventually also lead to deployment obstacles since QUIC stacks will
need to either base themselves on other TLS libraries, use a separate patched
OpenSSL build or require an update to a future OpenSSL version.

## Kernel e carico sulla CPU

Both Google and Facebook have mentioned that their wide scale deployments of
QUIC require roughly twice the amount of CPU than the same traffic load does
when serving HTTP/2 over TLS.

Some explanations for this include

- the UDP parts in primarily Linux is not at all as optimized as the TCP stack
  is, since it has not traditionally been used for high speed transfers like
  this.

- TCP and TLS offloading to hardware exist, but that is much rarer for UDP and 
  basically non-existing for QUIC.

There are reasons to believe that performance and CPU requirements will
improve over time.
