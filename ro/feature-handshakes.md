# Handshakes rapide

QUIC oferă stabilirea conexiunilor cu 0-RTT și 1-RTT, însemnând că, într-un 
scenariu ideal, QUIC nu face round-trip-uri în plus atunci când stabilește o 
conexiune. Cea mai rapidă metodă dintre cele două, handshake-ul 0-RTT, 
funcționează doar dacă a fost stabilită în trecut o conexiune la același host și 
o cheie secretă de la acea conexiune a fost salvată în cache.

## Informații din timp

QUIC permite unui sistem-client să includă informații deja în handshake-ul 
0-RTT. Această funcționalitate îi permite sistemului-client să livreze 
informații celuilalt sistem pe cât de repede este posibil, iar asta înseamnă, 
bineînțeles, că server-ul va răspunde și va trimite informații mai repede.
