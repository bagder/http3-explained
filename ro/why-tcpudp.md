## TCP sau UDP

Dacă nu putem să rezolvăm problema blocării vârfului de stivă din TCP, atunci, 
teoretic, ar trebui să putem să creăm un nou protocol de transport, diferit de 
UDP și TCP. Sau, poate chiar să folosim 
[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol),
care este un protocol de transport standardizat de IETF în [RFC4960]
(https://tools.ietf.org/html/rfc4960) și care include câteva dintre 
caracteristicile dorite.

Totuși, în ultimii ani, eforturile de a crea noi protocoale de transport au fost 
oprite aproape în totalitate de dificultățile în a le publica pe internet. 
Publicarea de noi protocoale este limitată de multe firewall-uri, NAT-uri, 
routere și alte middlebox-uri care permit doar conexiuni TCP și UDP între 
utilizatori și servere-le cu care au nevoie să comunicae. Introducerea unui 
nou protocol de transport face ca N% dintre conexiuni să eșueze pentru că sunt 
blocate de sisteme care văd că nu sunt UDP sau TCP, deci le consideră 
dăunătoare sau, pur și simplu, greșite. Rata de eșec de N% este considerată, 
deseori, prea mare pentru a merita efortul.

În plus, schimbările în layer-ul protocolului de transport al stivei de rețea, 
înseamnă, de obicei, protocoale implementate de kernel-urile sistemelor. 
Actualizarea și publicarea kernel-urilor sistemelor de operare este un proces 
încet, care presupune efort semnificativ. Multe îmbunătățiri ale TCP, 
standardizate de IETF, nu sunt publicate la scară largă sau folosite pentru că 
nu sunt implementate, în general.

## De ce nu SCTP-peste-UDP?

SCTP este un protocol de transport fiabil cu fluxuri șim pentru WebRTC, există 
deja implementări care îl folosesc peste UDP.

SCTP nu a fost considerat îndeajuns de bun față de QUIC din cauza câtorva 
motive, printre care:

 - SCTP nu rezolvă problema blocării vârfului de stivă pentru fluxuri
 - SCTP are nevoie ca numărul de fluxuri să fie predefinit la momentul stabilirii conexiunii
 - SCTP nu are o istorie puternică cu TLS/securitate
 - SCTP funcționează cu un handshake în 4 pași, în timp ce QUIC oferă 0-RTT
 - QUIC este un flux de octeți ca TCP, în timp ce SCTP se folosește de mesaje
 - Conexiunile QUIC pot migra între adrese IP, în timp ce ale SCTP nu

Pentru mai multe detalii legate de diferențe, vedeți [A Comparison between SCTP and
QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).
