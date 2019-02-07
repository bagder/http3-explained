## Protocollo di trasporto via UDP

QUIC è un protocollo di trasporto implementato su UDP. Se si osserva il
traffico di rete con un analizzatore di protocollo, il traffico QUIC appare
composto di pacchetti UDP.

Basato su UDP, utilizza anche i numeri di porta per identificare con precisione
un determinato servizio di rete su uno specifico indirizzo IP.

Tutte le implementazioni correnti e conosciute di QUIC sono sviluppate in
"user-space" il che permette una evoluzione più rapida rispetto ad una tipica
implementazione a livello di kernel-space.

## Funzionerà?

Ci sono aziende e altri setup di rete che bloccano il traffico UDP sulle porte
diverse dalla 53 (DNS). Altri rallentanto i flussi in maniera da influenzare
negativamente le prestazioni di QUIC, rendendolo piu lento che il TCP. Non vi
è limite alle manipolazioni che gli operatori di rete possono applicare.

Nel futuro prossimo, tutti gli impieghi di trasporto basato su QUIC dovranno
prevedere una modalita di fall-back indolore verso una modalità di trasporto
alternativa (basata su TCP). Gli ingegneri di Google hanno potuto misurare il
tasso di fallimento in percentuali a cifra singola, fra 2 e 5%.

## Apporterà miglioramenti?

Ci sono grosse probabilità che QUIC sia di valido aiuto al mondo Internet,
chiunque vorrà poterlo usare e ci si aspetterà di vederlo funzionare con
grande efficacia, fino al punto in cui le aziende cominceranno a considerare
il cambiamento. Negli anni e grazie agli sviluppi apportati a QUIC, il tasso
di successo nello stabilire connessioni QUIC è nettamente aumentato.
