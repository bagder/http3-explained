# API

Unul dintre motivele succesului pentru TCP-ul obșinuit și programele care îl 
folosesc este că folosesc un API de socket-uri standardizat. Are funcționalități 
bine definite și poți muta programe între sisteme de operare diferite, iar TCP 
funcționează la fel.

QUIC încă nu a ajuns la acest nivel. Nu există un standard de API pentru QUIC.

Cu QUIC, ai nevoie să alegi una dintre librăriile deja implementate și să 
rămâi la API-ul ei. Asta face, la un anumit nivel, ca aplicațiile să fie 
"legate" de o singură librărie. Schimbarea la o altă librărie înseamnă un alt 
API, iar asta poate implica foarte multă muncă.

De asemenea, de vreme ce QUIC este implementat, de obicei, în user-space, nu 
poate să extindă pur și simplu API-ul socket-urilor sau să arate la fel ca 
funcționalitățile existente TCP și UDP. Folosirea QUIC va însemna folosirea 
unui alt API decât cel al socket-urilor.
