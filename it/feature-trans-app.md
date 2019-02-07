## Livelli di Trasporto e Applicazione

Il QUIC di IETF è un protocollo di trasporto, sul quale altri protocolli
applicativi possono essere innestati. L'applicazione principale (iniziale)
di QUIC è al momento HTTP/3 (h3).

Il livello di trasporto supporta sia connessioni sia flussi.

La versione di QUIC sviluppata da Google presentava i layers di trasporto
e applicazione (HTTP) come fusi insieme all'interno di un singolo processo,
suonava molto come la "versione-speciale-che-manda-frames-http/2-via-udp".
