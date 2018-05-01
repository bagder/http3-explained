## TCP o UDP

Dato che non possiamo completamente mettere fine al bloccaggio ad inizio fila
all'interno di TCP, forse dovremmo essere in grado di sviluppare un nuovo 
protocollo di trasporto prossimo a UDO e TCP nello stack di rete. O magari 
impiegare [SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol)
che è un protocollo di trasporto standardizzato dalla IETF nella 
[RFC 4960](https://tools.ietf.org/html/rfc4960) contenente la maggior parte
delle caratteristiche necessarie allo scopo.

Al contrario, nel corso degli ultimi anni, tutti gli sforzi per progettare un
nuovo protocollo di trasporto sono stati sospesi a causa delle difficoltà
percepite nel distribuire tali protocolli all'interno di infrastrutture reali.
La quantità di firewalls, NATs, routers e altri dispositivi di rete che si 
iterpongono fra l'utente e il server sono semplicemente troppi, e sono a 
conoscenza dei soli UDP o TCP. Introdurre un altro protocollo di trasporto
fa si che un determinato tasso di connessioni N% fallisca, in quanto bloccato
dalle suddette middle-boxes che identificherebbero tale proto come malevolo,
malformato, nè TCP nè UDP. Un tasso di fallimento N% in ambito internet 
rappresenta spesso una buona ragione per non intraprendere alcuno sforzo.

In aggiunta, cambiare le cose a livello di "transport protocol layer" nello
stack di rete può spesso significare dover mettere mano al kernel del SO.
Modificare il kernel è un processo che richiede tempi lunghi, grandi sforzi e
non al riparo da pressioni. In anni recenti, abbiamo visto features di TCP
diventare standard IETF senza che vi sia stata corrispondenza -ad anni di
distanza- con il tasso di distribuzione degli stessi, per via della mancanza
di supporto universale.
