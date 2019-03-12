# Trimiterea de către server (Server push) în HTTP/3

Trimiterea de către server în HTTP/3 este similară cu cea descrisă în HTTP/2 ([RFC
7540](https://httpwg.org/specs/rfc7540.html)), dar folosește mecanisme diferite.

O trimitere de către server este, efectiv, răspuns la o cerere pe care un 
client nu a trimis-o niciodată!

Trimiterile de către server sunt permise numai dacă clientul a fost de acord cu 
ele. În HTTP/3, clientul stabilește o limită pentru cât de multe trimiteri 
acceptă, informqnd server-ul care este ID-ul maxim de flux. Trecerea peste acea 
limită va cauza o eroare de conexiune.

Dacă server-ul consideră probabil că clientul dorește o resursă în plus, pe care 
nu a cerut-o, dar pe care ar trebui să o aibă oricum, poate trimite un frame 
`PUSH_PROMISE` (prin fluxul de cerere) arătând cum arată cererea pentru care 
trimiterea este un răspuns, și apoi să trimită răspunsul în sine printr-un nou 
flux.

Chiar și atunci când s-a spus în prealabil că trimiterile sunt acceptate de 
către un client, fiecare flux individual poate fi anulat la orice moment dacă 
clientul consideră necesar. Atunci trimite un frame `CANCEL_PUSH` către server.

## Problematic

Încă de când această funcționalitate a fost discutată prima oară în dezvoltarea 
HTTP/2 și apoi, după ce protocolul a fost publicat pe internet, această 
funcționalitate a fost discutată, displăcută și lovită în nenumărate moduri 
pentru a o face utilizabilă.

Trimiterea nu este niciodată "gratuită", deoarece, chiar dacă salvează jumătate 
de round-trip, tot folosește lățime de bandă. Este deseori greu sau imposibil ca 
server-ul să știe cu un nivel ridicat de certitudine dacă o resursă ar trebui să 
fie trimisă sau nu.
