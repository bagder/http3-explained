# Flussi QUIC e HTTP/3

HTTP/2 è stato costretto a concepire il proprio schema di flussi e
multiplexing basandosi su TCP, mentre HTTP/3 è studiato per lavorare con
QUIC e quindi trae massimo vantaggio dall'utilizzo degli streams.

Le richieste HTTP veicolate su HTTP/3 sfruttano un set di flussi specifico.

## Frames HTTP/3

Dialogare in HTTP/3 implica l'attivazione di un flusso QUIC e l'invio di
una serie di frames all'altro capo della connessione. Esistono al momento
(alle 9 del 18 Dicembre 2018) una serie abbastanza limitata di frames
predefiniti in HTTP/3. I più rilevanti sono seza dubbio:
- HEADERS, si occupano di comprimere e spedire le intestazioni
- DATA, tratta l'invio di dati binarii
- GOAWAY, pregasi terminare la connessione

## Richiesta HTTP

Il client invia la propria richiesta HTTP su un flusso QUIC *bidirezionale*
iniziato dal client. 

Una richiesta consiste di un singolo frame HEADERS e può essere seguita da
uno o due frames aggiuntivi: una serie di frames DATA ed eventualmente un
frame finale contenente gli HEADERS di coda.

Dopo aver spedito la propria richiesta, il client termina il flusso in uscita.

## Risposta HTTP

Il server replica spedendo la risposta HTTP sullo stream bidirezionale. Un
frame HEADERS, una serie di DATA ed eventualmente un frame HEADERS di coda.

## Intestazioni QPACK

I frames HEADERS contengono le intestazioni HTTP compresse con l'algoritmo
QPACK. QPACK risulta simile al vecchio HPACK utilizzato in HTTP/2 ([RFC 7541
](https://httpwg.org/specs/rfc7541.html)), benché modificato per consegnare
i differenti flussi in modalità "disordinata" (out-of-order).

QPACK si avvale di due streams QUIC unidirezionali fra i due estremi della
connessione. Tali streams sono utilizzati per trasportare la tabella
dinamica di compressione nelle due direzioni opposte.
