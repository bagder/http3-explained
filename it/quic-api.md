# API

Uno dei fattori del successo del classico TCP e dei programmi su di esso
basati è stata la disponibilita di API socket standardizzazate. Poter
offrire funzionalità ben definite usando tali API permette di "portare"
programmi fra diversi sistemi operativi dato che TCP funziona in maniera
identica indipendentemente dalla piattaforma.

QUIC non è ancora arrivato a quel punto. Non esistono API standard in QUIC.

Con QUIC, ci si deve basare su una delle librerie esistenti e fare
affidamento alle API fornite dalla libreria scelta. Ciò fa si che le
applicazioni siano "abbinate" ad una singola libreria, almeno in teoria.
Cambiare ed adottare un'altra libreria signigica nuove API e potrebbe
richiedere molto lavoro di adattamento.

Inoltre, dato che QUIC è spesso implementato in user-space, non è adatto
ad estendere le API socket o offrire funzionalità in qualche modo simili agli
attuali TCP e UDP. Usare QUIC significa utilizzare un'API esterna al socket.
