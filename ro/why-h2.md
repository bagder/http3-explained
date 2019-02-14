## Vă mai aduceți aminte de HTTP/2?

Specificația HTTP/2, [RFC 7540](https://httpwg.org/specs/rfc7540.html), a fost 
publicată în mai 2015, iar, de atunci, protocolul a fost implementat și publicat
la o scară largă pe internet și pe World Wide Web.

La începutul lui 2018, aproape 40% din primele 1000 de pagini de internet din 
lume rulau pe HTTP/2, aproximativ 70% din toate cererile HTTPS făcute de
Firefox primeau răspunsuri HTTP/2, iar toate browsere-le, servere și proxy-uri
ofereau suport pentru el.

HTTP/2 rezolvă o multitudine de neajunsuri ale HTTP/1 și, o dată cu introducerea
 celei de-a doua versiuni a HTTP, utilizatorii se pot opri din a folosi unele 
metode neoficiale menite să rezolve aceste neajunsuri. Câteva dintre aceste 
metode sunt destul de dificile pentru programatorii web.

Una dintre funcționalitățile principale ale HTTP/2 este că se folosește de 
multiplexing, astfel încât mai multe fluxuri logice sunt trimise peste aceeași
conexiune TCP. Acest lucru face ca totul să se întâmple mai bine și mai repede.
Efortul pentru controlul congestionărilor este mai bun, iar utilizatorii au 
posibilitatea să folosească conexiunile TCP mult mai bine și, deci, să satureze
corespunzător lărgimea de bandă. Astfel, conexiunile TCP sunt active mai multe,
ceea ce este bine pentru că ajung la viteza maximă mult mai frecvent ca înainte.
Compresia headere-lor ajută conexiunile să folosească mai puțină lărgime de 
bandă.

Prin HTTP/2, browsere-le folosesc, de obicei, *o conexiune* TCP pentru fiecare
host, în loc de cele *șase conexiuni* folosite în trecut. De fapt, tehnicile 
de contopire și "desharding" ale conexiunilor, folosite cu HTTP/2, pot reduce
numărul de conexiuni și mai mult de atât.

HTTP/2 a reparat și problema pe care protocolul o avea cu blocarea primei 
poziții a stivei (head of line blocking), în urmă căreia clienții trebuia să
aștepte ca prima cerere din stivă să fie finalizată înainte ca următoarea 
cerere să poată fi trimisă.

![http2 man](../images/h2-man.jpg)
