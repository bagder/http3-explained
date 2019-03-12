## IETF

Grupul de lucru QUIC, care a fost organizat pentru a standardiza protocolul în 
interiorul IETF, a decis repede că acesta ar trebui să poată să transfere și alte 
protocoale în afară de "doar" HTTP. Google-QUIC nu a transferat niciodată 
altceva în afară de HTTP. În practică, a transferat frame-uri HTTP/2, 
folosindu-se de sintaxa pentru frame-uri a HTTP/2.

S-a spus, de asemenea, că IETF-QUIC ar trebui să își bazeze criptarea și 
securitatea pe TLS 1.3, în loc de implementarea "proprie" folosită de 
Google-QUIC.

Ca să îndeplinească cerință de trimite-mai-mult-decât-HTTP, arhitectura 
protocolului QUIC al IETF a fost separată în două părți: transferul QUIC și 
"HTTP peste QUIC". A doua parte este numită uneori și "hq".

Această despărțire, chiar dacă sună inofensivă, a făcut ca specificația 
IETF-QUIC să difere destul de mult de cea originală, Google-QUIC.

Grupul de lucru a decis repede, totuși, că, pentru a putea avea puterea de 
concentrare și abilitatea de a livra versiunea 1 a QUIC, se va ocupa de 
livrarea HTTP, lăsând transferurile non-HTTP pe mai târziu.

În martie 2018, când am început să lucrez la această carte, planul era ca 
specificația finală a versiunii 1 să fie publicată în noiembrie 2018. Această 
dată a fost amânată până în iulie 2019.

În timp ce munca la IETF-QUIC a progresat, echipa de la Google a implementat
deja detalii din versiunea IETF și a început să migreze versiunea proprie a 
protocolului către ce ar putea să devină versiunea IETF. Google au continuat să 
își folosească propria versiune a QUIC în browser și servicii.

[Majoritatea implementărilor în curs de desfășurare]
(https://github.com/quicwg/base-drafts/wiki/Implementations) au decis să se 
concentreze pe versiunea IETF și nu sunt compatibile cu versiunea Google.
