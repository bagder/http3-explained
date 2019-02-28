## User-space

Implementarea unui protocol de transfer în user-space ajută la iterarea rapidă 
a protocolului, deoarece evoluția protocolului este mult mai ușoară fără 
necesitatea ca aplicațiile-client și servere-le să își actualizeze kernel-ul 
sistemului de operare pentru a publica noi versiuni.

Nu există nimic inerent în QUIC care să îl împiedice să fie implementat și 
oferit prin kernel-urile sistemelor de operare în viitor, dacă cineva va 
considera că asta este o idee bună.

### Mai multe implementări

Un efect evident al implementării protocolului de transport în user-space este 
că ne putem aștepta să vedem multe implementări independente.

Diferitele aplicații vor include probabil (sau vor fi construite ca un strat 
deasupra a) diferite implementări HTTP/3 și QUIC în viitorul previzibil.
