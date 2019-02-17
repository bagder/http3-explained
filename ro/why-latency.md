# Informații din timp

QUIC oferă handshake-uri 0-RTT și 1-RTT care reduc timpul necesar negocierii și 
stabilirii unei noi conexiuni. În comparație, TCP folosește un handshake în trei 
pași.

În plus, QUIC oferă suport pentru "informații din timp", care îi dau 
posibilitatea să transmită mai multe informații și este folosit mult mai ușor 
decât TCP Fast Open.

Folosindu-se conceptul de fluxuri, o nouă conexiune logică poate fi deschisă 
către același host fără a fi nevoie să se aștepte terminarea uneia existente.

## TCP Fast Open este problematic

TCP Fast Open a fost publicat ca [RFC 7413](https://tools.ietf.org/html/rfc7413) 
în decembrie 2014, iar specificația descrie cum pot programele transmite 
informații către un server, livrându-le deja în primul pachet TCP SYN.

Implementarea acestei componente în realitate a durat mult timp și este plină de 
probleme, chiar și acum în 2018. Cei care implementează specificația TCP au 
avut probleme și, astfel, și programele care încearcă să folosească această 
funcționalitate au avut la fel - în primul rând în a ști ce sisteme de operare 
să activeze și apoi cum să anuleze schimbările atunci când au apărut probleme. 
Au fost identificate câteva rețele care au interferat cu traficul TCP Fast Open, 
stricând, deci, permanent, astfel de TCP handshakes.