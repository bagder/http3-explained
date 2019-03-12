## Protocolul de transfer peste UDP

QUIC este un protocol de transfer implementat peste UDP. Dacă vă urmăriți 
traficul rețelei, o să vedeți că QUIC apare ca pachete UDP.

Tot bazându-se pe UDP, folosește apoi port-uri UDP pentru a identifica servicii 
de rețea specifice care rulează la o anumită adresă IP.

Toate implementările QUIC cunoscute sunt, acum, în user-space, ceea ce permite 
o evoluție mult mai rapidă decât permit implementările kernel-space.

## Va funcționa?

Există organizații și alte structuri de rețele care blochează traficul UDP pe 
alte porturi decât 53 (folosit pentru DNS). Altele limitează astfel de date în 
feluri care fac ca QUIC să funcționeze mai greu ca protocoalele bazate pe TCP. 
Nu există limite la ce pot face unii operatori.

În viitorul predictibil, toate transferurile bazate pe QUIC va trebui să poată 
să regreseze (fall-back) la alte alternative (bazate pe TCP). Inginerii Google 
au menționat în trecut rate de eșec de ordinul numerelor cu o singură cifră.

## Se va îmbunătăți?

Șansele sunt ca, dacă QUIC se dovedește să fie o adiție valoroasă pentru 
internet, oamenii să vrea să îl folosească și să funcționeze în rețelele lor, 
iar atunci companiile își vor reconsidera obstacolele. În timpul anilor de 
dezvoltare, rata de succes în a stabili și folosi conexiuni QUIC pe internet a 
crescut.
