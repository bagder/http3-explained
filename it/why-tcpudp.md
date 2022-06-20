## TCP o UDP

Dato che non possiamo completamente mettere fine al bloccaggio ad inizio fila
all'interno di TCP, dovremmo almeno essere in grado di sviluppare un protocollo
di trasporto più vicino a UDP e TCP nello stack di rete. O magari impiegare [SCTP
](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol) che è un
protocollo di trasporto standardizzato dalla IETF nella [RFC 4960
](https://tools.ietf.org/html/rfc4960), contenente la maggior parte delle
caratteristiche o funzioni necessarie allo scopo.

Al contrario, nel corso degli ultimi anni, tutti gli sforzi per progettare un nuovo
protocollo di trasporto sono stati sospesi a causa delle difficoltà percepite nel
distribuire tali protocolli all'interno di infrastrutture reali. La quantità di
firewalls, NATs, routers e altri dispositivi di rete che si iterpongono fra l'utente
e il server sono semplicemente troppi, e sono a conoscenza dei soli UDP o TCP.
Introdurre un altro protocollo di trasporto fa si che un determinato tasso di
connessioni N% fallisca, in quanto bloccato dalle suddette middle-boxes che
identificherebbero tale proto come malevolo, malformato, né TCP né UDP. Un tasso di
fallimento N% in ambito internet rappresenta spesso una buona ragione per non
intraprendere alcuno sforzo.

In aggiunta, cambiare le cose a livello di "transport protocol layer" nello stack di
rete può spesso significare dover mettere mano al kernel del SO. Modificare il kernel
è un processo che richiede tempi lunghi, grandi sforzi e non al riparo da pressioni.
In anni recenti, abbiamo visto features di TCP diventare standard IETF senza che vi
sia stata corrispondenza -ad anni di distanza- con il tasso di distribuzione degli
stessi, per via della mancanza di utilizzo o di supporto universale.

## Perché no, SCTP-over-UDP

SCTP è un protocollo di trasporto di flussi affidabile, ed esistono persino alcune
implementazioni in ambito WebRTC che utilizzano SCTP via UDP.

Non fu dunque scelto come valida base per QUIC per via di molteplici ragioni, ossia:

 - SCTP non risolve il problema del "blocco di inizio riga" con i flussi
 - SCTP richiede una decisione sul numero di streams nella fase di inizializzazione
 - SCTP non ha un passato particolarmente brillante in quanto a sicurezza TLS
 - SCTP utilizza una negoziazione a 4 vie, mentre QUIC ne offre una da 0-RTT
 - QUIC è un flusso di bytes ordinato al pari di TCP, SCTP un protocollo a messaggi
 - Una connessione QUIC può essere migrata fra indirizzi IP, ma SCTP non lo permette

Per maggiori dettagli relativi alle differenze, vedere [Un raffronto tra SCTP e QUIC
](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).
