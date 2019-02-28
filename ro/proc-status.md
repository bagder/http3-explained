# Starea curentă

Grupul de lucru QUIC a muncit asiduu începând cu sfârșitul lui 2016 pentru a 
specifica particularitățile protocolului, iar planul este ca totul să fie gata 
până în iulie 2019.

La timpul scrierii acestui text, în noiembrie 2018, încă nu există teste de 
interoperabilitate la scară largă pentru HTTP/3 - există doar două implementări 
majore, și niciuna dintre ele nu este făcută de un browser sau de un software 
open-source popular.

Există 15 [implementări QUIC]
(https://github.com/curl/curl/wiki/QUIC-implementation) înregistrate în paginile 
wiki ale grupului de lucru, dar foarte puține dintre ele pot funcționa pe 
ultimele modificări ale schiței specificației.

Implementarea QUIC nu este ușoară și protocolul a fost actualizat încontinuu, 
schimbându-se chiar și la această dată.

## Servere

Nu a fost făcut niciun anunț public de implementare a QUIC de către Apache sau 
ngnix.

## Programele-client

Niciunul dintre browsere-le mari nu a publicat până acum vreo versiune, în orice 
stare, care să poată să ruleze versiunea IETF a QUIC sau HTTP/3.

Google Chrome este publicat deja de mulți ani cu o implementare funcțională a 
propriei implementări QUIC, dar funcționalitățile ei nu sunt compatibile cu 
protocolul dezvoltat de IETF, iar implementarea lor pentru HTTP/3 este diferită.

## Obstacolele din calea implementării

Pentru QUIC, s-a decis folosirea TLS 1.3 ca fundație pentru criptare și layer-ul 
de securitate (pentru a evita inventarea a ceva nou, comunicarea bazându-se, în 
schimb, pe un protocul de încredere deja existent. Totuși, făcând asta, grupul 
de lucru a decis, de asemenea, ca pentru a optimiza folosirea TLS în QUIC, 
acesta ar trebui să folosească numai "mesaje TLS" și nu "înregistrări TLS".

Chiar dacă sună ca o schimbare inofensivă, această decizie a pus piedici 
semnificative multora dintre cei care implementează QUIC. Librăriile software 
care implementează TLS 1.3 pur și simplu nu au destule API-uri pe care să le 
expună pentru ca QUIC să le acceseze. În timp ce câțiva dintre cei care 
implementează vin din organizații mai mare care lucrează la propria stivă TLS 
în paralel, acest lucru nu se aplică la toată lumea.

Bine-cunoscutul OpenSSL, de exemplu, nu implementează niciun API în acest moment 
și nu a făcut niciun anunț care să exprime planuri în această direcție în 
viitorul apropiat (afirmație valabilă în noiembrie 2018).

Asta va duce, eventual, și la obstacole în calea implementării din cauză că 
QUIC va avea nevoie fie să se bazeze pe alte librării TLS, fie să folosească 
o versiune separată și modificată a OpenSSL, fie să ceară o actualizare a 
viitoarelor versiune OpenSSL.

## Kernel-uri și capacitatea de procesare

Și Google și Facebook au menționat că implementările proprii la scară largă ale 
QUIC vor necesita aproximativ dublul capacității de procesare (CPU) față de 
același trafic servit prin HTTP/2 peste TLS.

Câteva explicatii pentru asta sunt:
- componenta UDP, mai ales în Linux, nu este deloc optimizată la fel cum este
  stiva TCP, deoarece nu a fost folosită în mod normal pentru transferuri de 
  mare viteză.
- Pentru TCP și TLS există descărcare către hardware (offloading to hardware), 
  dar pentru UDP exemplele sunt mult mai rare, iar pentru QUIC este practic 
  inexistentă.
  
Există motive să credem că performanța și cerințele CPU se vor îmbunătăți cu 
timpul.
