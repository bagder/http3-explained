## În aceeași ordine

QUIC garantează livrarea în aceeași ordine a fluxurilor în sine, dar nu și 
între fluxuri. Asta înseamnă că fiecare flux va trimite informații și va menține 
ordinea informațiilor, dar fluxurile pot ajunge la destinație în altă ordine 
decât cea în care au fost trimise de la sursă.

De exemplu: fluxul A și B suntr transferate de la server către un program. 
Fluxul A este început primul și apoi fluxul B. În QUIC, un pachet pierdut 
afectează doar fluxul căruia îi aparține. Dacă fluxul A pierde un pachet, dar 
fluxul B nu, fluxul B își poate continua și finaliza transferul, în timp ce 
pachetul pierdut de fluxul A este retransmis. Acest lucru nu era posibil cu 
HTTP/2.

Ilustrat aici cu două fluxuri, unul galben și unul albastru, trimise între 
două sisteme QUIC, peste o singură conexiune. Fluxurile sunt independente și 
pot ajunge la destinație într-o ordine diferită, dar fiecare dintre ele este 
livrat cu siguranță.

![două fluxuri QUIC între două computere](../images/quic-chain-streams.png)
