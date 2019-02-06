## TCP o UDP

Dato che non possiamo completamente mettere fine al bloccaggio ad inizio fila
all'interno di TCP, forse dovremmo essere in grado di sviluppare un nuovo protocollo
di trasporto prossimo a UDO e TCP nello stack di rete. O magari impiegare [SCTP
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
identificherebbero tale proto come malevolo, malformato, nè TCP nè UDP. Un tasso di
fallimento N% in ambito internet rappresenta spesso una buona ragione per non
intraprendere alcuno sforzo.

In aggiunta, cambiare le cose a livello di "transport protocol layer" nello stack di
rete può spesso significare dover mettere mano al kernel del SO. Modificare il kernel
è un processo che richiede tempi lunghi, grandi sforzi e non al riparo da pressioni.
In anni recenti, abbiamo visto features di TCP diventare standard IETF senza che vi
sia stata corrispondenza -ad anni di distanza- con il tasso di distribuzione degli
stessi, per via della mancanza di supporto universale.

If we can't fix head-of-line blocking within TCP, then in theory we should
be able to make a new transport protocol next to UDP and TCP in the network
stack. Or perhaps even use
[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol)
which is a transport protocol standardized by the IETF in [RFC
4960](https://tools.ietf.org/html/rfc4960) with several of the desired
characteristics.

However, in recent years efforts to create new transport protocols have almost
entirely been halted because of the difficulties in deploying them on the Internet. 
Deployment of new protocols is hampered by many firewalls, NATs, routers and other 
middle-boxes that only allow TCP or UDP are deployed between users and the servers 
they need to reach. Introducing another transport protocol makes N% of the connections
fail because they are being blocked by boxes that see it not being UDP or TCP and 
thus evil or wrong somehow. The N% failure rate is often deemed too high to be 
worth the effort.

Additionally, changing things in the transport protocol layer of the network
stack typically means protocols implemented by operating system kernels.
Updating and deploying new operating system kernels is a slow process that
requires significant effort. Many TCP improvements standardized by the IETF
are not widely deployed or used because they are not broadly supported.

## Why not SCTP-over-UDP

SCTP is a reliable transport protocol with streams, and for WebRTC there are
even existing implementations using it over UDP.

This was not deemed good enough as a QUIC alternative due to several reasons,
including:

 - SCTP does not fix the head-of-line-blocking problem for streams
 - SCTP requires the number of streams to be decided at connection setup
 - SCTP does not have a solid TLS/security story
 - SCTP has a 4-way handshake, QUIC offers 0-RTT
 - QUIC is a bytestream like TCP, SCTP is message-based
 - QUIC connections can migrate between IP addresses but SCTP cannot

Per maggiori dettagli relativi alle differenze, vedere [Un raffronto tra SCTP e QUIC
](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).
