# Adresele HTTPS://

HTTP/3 va rula folosind adrese `HTTPS://`. Lumea este plină de aceste URL-uri și 
a fost stabilit nepractic și cu totul nerezonabil să se introducă o nouă schemă 
de URL pentru noul protocol. Cum HTTP/2 nu a avut nevoie de o nouă schemă, nici 
HTTP/3 nu va avea nevoie.

Complexitatea adăugată în situația HTTP/3 este, totuși că, în timp ce HTTP/2 a 
fost o modalitate complet nouă de a transfera HTTP, era în continuare bazat pe 
TLS și TCP, la fel cum era și HTTP/1. Faptul că HTTP/3 este făcut peste QUIC 
schimbă lucurile în câteva aspecte importante.

Adresele tradiționale, în text clar, `HTTP://` for fi lăsate așa cum sunt și, pe 
măsură ce avansăm într-un viitor cu transferuri mai sigure, vor fi folosite din 
ce în ce mai puțin frecvent. Cererile către astfel de URL-uri pur și simplu nu 
vor fi actualizate să folosească HTTP/3. În realitate, sunt rareori actualizate 
să folosească chiar și HTTP/2, dar din cu totul alte motive.

## Conexiunea inițială

Prima conexiune către o gazdă nouă, nefolosită în trecut pentru un URL HTTPS://,
 va fi făcută, probabil, peste TCP (posibil, în plus față de o încercare 
paralelă de conectare prin QUIC). Gazda poate fi un server tradițional, fără 
suport pentru QUIC sau poate exista un middlebox care ridică obstacole care 
previn successul conexiunii QUIC.

O aplicație-client și un server moderne vor negocia, presupus, HTTP/2 în primul 
handsjake. Când conexiunea a fost stabilită și server-ul răspunde la o cerere 
HTTP de la client, el îi poate spune clientului despre ce capacilități are și 
despre o preferință pentru HTTP/3.
