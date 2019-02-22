# Bit-ul rotativ (Spin Bit)

Una dintre cele mai lungi discuții de design din cadrul grupului de lucru QUIC, 
care a fost subiectul a câtorva sute de ore de e-mail-uri și ore de discuție, se 
referă la un singur bit: Bit-ul rotativ.

Susținătorii acestui bit insită e nevoie ca operatorii și oamenii, care sunt pe 
drumul dintre două capete ale unei conexiuni QUIC, să poată să măsoare timpii de 
încărcare.

Opozanților acestei funcționalități nu le plac potențialele pierderi de 
informații.

## Rotirea unui bit

Ambele capete, aplicația-client și server-ul, mențin o valoare de rotație, 0 
sau 1, pentru fiecare conexiune QUIC, și setează valoarea potrivită pe bit-ul 
rotativ în pachetele pe care le trimite.

Ambele părți, apoi, trimit pachete cu acel bit rotatic setat pe aceeași valoare, 
pe toată durata unui drum dus-întors și apoi comută valoarea. Efectur este, apoi, 
un puls de unu și zero în câmpul acelui bit, pe care observatorii îl pot 
monitoriza.

Această măsurătoare funcționează doar când expeditorului nu îi sunt limitate 
nici aplicația nici debitul, iar reordonarea pachetelor în rețea, poate face 
ca informațiile neclare.
