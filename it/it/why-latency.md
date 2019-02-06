# Dati in anticipo

QUIC offre entrambe le negoziazioni 0-RTT e 1-RTT al fine di minimizzare il
tempo necessario alla negoziazione e setup della connessione. Paragoniamolo
all'handshake a 3 vie del TCP.

In aggiunta a ciò QUIC mette a disposizione il supporto per  "dati anticipati"
sin da subito, per permettere un flusso di dati più intenso, oltre a
risultare di semplice impiego rispetto all'opzione "TCP Fast Open"

Con il concetto di stream, un'altra connessione logica verso uno stesso host
può essere effettuata direttamente senza aspettare che la prima abbia finito.

## Il "TCP Fast Open" è problematico

TCP FO è stato pubblicato come [RFC 7413](https://tools.ietf.org/html/rfc7413)
nel Dicembre 2014; tale specifica descrive come le applicazioni possano
inviare dati al server gia a partire dal primo pacchetto TCP SYN.

Arrivare ad un supporto mondiale per tale opzione ha necessitato lungo tempo,
e siamo ancora vittime di malfunzionamenti nel 2018. Coloro i quali hanno
implementato lo stack TCP hanno evidenziato svariati problemi, cosi come le
applicazioni che tentavano di trare vantaggio da tale caratteristica - sia nel
comprendere su quali versioni del Sistema Operativo attivarla sia nel tentare
di risolvere problemi inerenti la mancanza di supporto lato client (backdown).
Molte reti sono state segnalate per l'interferenza al traffico TFO, ed hanno
quindi inficiato il buon funzionamento della negoziazione TCP.
