## Trasferimento di dati affidabile

Mentre sappiamo che UDP non è un modo di trasporto affidabile, notiamo come
QUIC aggiunga uno strato di controllo, garantendo infine l'affidabilità.
Offre retrasmissione di pacchetti, controllo della congestione, regolazione
di flusso e altre caratteristiche gia presenti nel TCP.

I dati spediti attraverso QUIC da un end-point saranno trasportati prima o
poi all'altro capo della connessione, tanto che quest'ultima sia mantenuta.
