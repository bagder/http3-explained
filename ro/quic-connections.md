# Conexiuni

O conexiune QUIC este o singură conversație între două sisteme QUIC. Stabilirea 
conexiunii QUIC combină negocierea versiunii cu handshake-urile criptografice și 
de transport pentru a reduce timpii de încărcare.

Pentru a trimite efectiv informații prin acest tip de conexiune, unul sau mai 
multe fluxuri trebuie să fie create și folosite.

## ID-ul conexiunii

Fiecare conexiune deține un set de identificatori, sau ID-uri de conexiune, iar 
fiecare dintre ei poate fi folosit pentru a identifica o conexiune. ID-urile de 
conexiune sunt alese independent de capetele conexiunii; fiecare capăt alege 
ID-urile pe care le folosește celălalt capăt.

Funcționalitatea principală a acestor ID-uri de conexiune este să se asigure că 
schimbările de adresare ale protocoalelor din layere-le de dedesubt (UDP, IP și 
mai jos) nu cauzează ca pachetele unei conexiuni QUIC să fie livrate către un 
alt sistem.

Profitând de ID-uri, conexiunile pot, deci, migra între adrese de IP și 
interfețe de rețea în moduri în care TCP nu putea. De exemplu, migrația permite 
ca download-uri în curs de desfășurare să se mute de la o conexiune la o 
rețea celulară la una mai rapidă peste wifi atunci când utilizatorul își aduce 
device-ul într-un loc care oferă wifi. Similar, download poate continua peste 
rețeaua celulară dacă cea wifi devine indisponibilă.

## Port-urile

QUIC este construit peste UDP, așa că un număr de port pe 16 biți este folosit 
pentru a diferenția conexiunile primite.

## Negocierea versiunii

O cerere de conexiune QUIC venită de la o aplicație-client o să îi spună 
server-ului ce versiune de protocol QUIC vrea să folosească, iar server-ul va 
răspunde cu o listă de versiuni din care aplicația poate alege.
