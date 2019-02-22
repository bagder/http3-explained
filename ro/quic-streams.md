# Fluxuri

Fluxurile în QUIC oferă o abstractizare simplă a unui flux de octeți ordonat.

Există două tipuri de fluxuri de bază în QUIC:

 - Fluxuri unidirecționale care transferă informațiile într-o singură direcție: 
   de la inițiatorul fluxului la receptor.
 
 - Fluxuri bidirecționale care permit ca informațiile să fie transmise în 
   ambele direcții.

Oricare tip de flux poate fi creat de oricare dintre capetele conexiunii, poate 
trimite informații amestecat cu alte fluxuri și poate fi anulat.

Pentru a trimite date printr-o conexiune QUIC, unul sau mai multe fluxuri sunt 
folosite.

## Controlul debitului

Debitul fluxurilor este controlat individual, permițqnd ca unul dintre capete să 
limiteze memoria alocată și să aplice presiune înapoi. Crearea de fluxuri are, 
de asemenea, debitul controlat, cu fiecare dintre sisteme declarând ID-ul maxim 
pe care este dispus să îl accepte la un moment dat.

## Identificatorii fluxurilor

Fluxurile sunt identificate de un integer unsigned pe 62 de octeți, numit și 
ID-ul fluxului (Stream ID). Cei mai puțini semnificativi doi octeți ai ID-ului 
sunt folosiți pentru identificarea tipului fluxului (unidirecțional sau 
bidirecțional) și inițiatorul fluxului.

Cel mai puțin semnificativ bit (0x1) al id-ului identifică inițiatorul fluxului. 
Aplicațiile-client inițiază fluxuri folosind numere pare (acelea cu cel mai 
puțin semnificativ bit setat pe 0); servere-le inițiază fluxuri folosind numere 
impare (cu bitul setat pe 1);

Al doilea cel mai puțin semnificativ bit (0x2) al ID-ul fluxului diferențiază 
între fluxuri unidirecționale și bidirecționale. Fluxurile unidirecționale au 
acest bit setat pe 1, iar fluxurile bidirecționale au acest bit setat pe 0.

## Paralelismul fluxurilor

QUIC permite ca un număr arbitrar de fluxuri să funcționeze în paralel. Un capăt 
al conexiunii limitează numărul de fluxuri paralele active prin limitarea 
ID-ului maxim pe care îl poate avea un flux.

ID-ul maxim al fluxului este specific fiecărui capăt și se aplică numai 
sistemului care primește această setare.

## Trimiterea și primirea de informații

Sistemele folosesc fluxuri ca să trimită și să primească informații. Acesta 
este, în fond, scopul lor principal. Fluxurile sunt abstracții de octeți 
ordonați. Fluxurile separate nu sunt, totuși, livrate în ordinea originală.

## Prioritizarea fluxurilor

Multiplexing-ul fluxurilor are un efect semnificativ asupra perfomanțelor 
aplicației dacă resursele alocate fluxului nu sunt corect prioritizate. 
Experiența cu alte protocoale care fac multiplexing, cum ar fi HTTP/2, arată că 
strategiile de prioritizare eficiente au un efect pozitiv asupra performanței.

QUIC, în sine, nu oferă cadre pentru prioritizarea informației. În schimb, se 
bazează pe primirea prioritizării de la aplicația care folosește QUIC. 
Protocoalele care folosesc QUIC au posibilitatea de a defini orice schemă de 
prioritizare care se potrivește semanticii proprii.

Când HTTP/3 este folosit peste QUIC, prioritizarea este făcută în layer-ul 
HTTP.
