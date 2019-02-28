# Fluxurile QUIC și HTTP/3

HTTP/3 este făcut pentru QUIC, așa că profită la maxim de fluxurile QUIC, în 
timp ce HTTP/2 a trebuit să își proiecteze întregul conept de fluxuri și 
multiplexing peste TCP.

Cererile HTTP făcute peste HTTP/3 folosesc un set specific de fluxuri.

## Frame-uri HTTP/3

HTTP/3 înseamnă stabilirea unor fluxuri QUIC și trimiterea unui set de frame-uri 
către celălalt capăt. Există un număr mic de frame-uri (de fapt doar nouă pe 
data de 18 decembrie 2018!) cunoscute în HTTP/3. Cele mai importante sunt, 
probabil:

- HEADERS, care trimite headere HTTP compresate
- DATA, trimite conținut binar
- GOAWAY, te rog închide această conexiune

## Cererea HTTP

Clientul își trimite cererea HTTP printr-un flux QUIC bidirecțional inițiat de 
client.

O cerere este formată dintr-un singur frame HEADERS și poate, opțional, fi 
urmat de unul sau două alte frame-uri: o serie de frame-uri DATA și, posibil, 
un frame HEADERS final pentru trailers [date decalate].

După ce a trimis o cerere, un client închide fluxuri pentru trimiteri.


## Răspunsul HTTP

Server-ul trimite înapoi răspunsul său HTTP pe un flux bidirecțional. Un frame 
HEADERS, o serie de frame-uri DATA și, posibil, un frame HEADERS decalat.

## Headere-le QPACK

Frame-urile HEADERS conțin headere HTTP compresate folosind algoritmul QPACK. 
QPACK este similar în stil cu algoritmul de compresie al HTTP/2 numit HPACK ([RFC
7541](https://httpwg.org/specs/rfc7541.html)), dar modificat să lucreze cu 
fluxuri trimise neordonat.

QPACK în sine folosește două fluxuri QUIC unidirecționale între două sisteme. 
Sunt folosite pentru a transfera infomații tabulare dinamice în oricare direcție.
