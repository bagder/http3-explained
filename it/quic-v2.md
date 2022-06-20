# QUIC v2

Per potersi concentrare il più possibile sul cuore del protocollo QUIC ed
essere in grado di consegnarlo per tempo, diverse opzioni che inizialmente
avrebbero dovuto essere incluse come base del procollo hanno purtroppo
dovuto essere posticipate fino al punto da essere state pianificate in una
versione successiva di QUIC. Appunto, QUIC versione 2 o maggiore.

L'autore di questo documento dispone di una sfera di cristallo non proprio
perfetta, quindi non può predire esattamente quali di queste caratteristiche
saranno o meno integrate nella versione 2. Possiamo tuttavia citare alcune
delle opzioni esplicitamente rimosse dalla v1 -per essere sviluppate in un
secondo momento- opzioni che potrebbero perciò essere presenti nella v2.

## Correzione dell'errore anticipata (Forward Error Correction)

La FEC (Forward Error Correction) è un metodo di controllo d'errore relativo
alle trasmissioni dati in cui un emissario (sender) spedisca una quantità di
dati ridondante e in cui il ricevente (receiver) riconosca solamente la
porzione di dati che non contenga alcun errore apparente.

Google ha sperimentato questa tecnica nella sua implementazione originaria di
QUIC ma fu successivamente rimossa in quanto gli esperimenti non diedero
risultati soddisfacenti. Questa opzione è soggetta a discussione per entrare
nella seconda versione di QUIC, ma necessita di argomenti a proprio favore
nel mostrare che non penalizzi o influenzi negativamente le prestazioni.

## Multipath

Il "multipath" è una tecnica di trasporto che per definizione utilizza percorsi
di rete complementari (multipli ed alternativi) al fine di massimizzare
l'utilizzo delle risorse ed aumentarne l'affidabilità attraverso la ridondanza.

I fautori e sostenitore di SCTP tengono a sottolineare come SCTP contempli gia
il multipath, così come il TCP più moderno.

## Dati inaffidabili

È stato proposto di offrire streams "non-affidabili" come opzione, il che
permetterebbe a QUIC di rimpiazzare qualsiasi applicazione che utilizzi UDP.

## Adattamenti che non riguardano HTTP

DNS over QUIC è stato uno dei protocolli non-HTTP di cui si è parlato per
primo, e al quale probabilmente sarà dedicata molta attenzione una volta che
QUIC v1 e HTTP/3 saranno consegnati al pubblico. Ovviamente, con la nascita di
un nuovo tipo di trasporto come questo, sono sicuro che il campo di applicazione
non si limiterà al solo DoQ.
