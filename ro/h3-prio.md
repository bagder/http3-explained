# Prioritizarea HTTP/3

Unul dintre frame-urile fluxurilor HTTP/3 se numește `PRIORITY`. Este folosit ca 
să se stabilească prioritatea și dependințele pe un flux într-un mod similar cu 
modul de funcționare din HTTP/2.

Frame-ul poate stabili că un flux specific depinde un alt flux specific și poate 
da unui anumit flux "greutate".

Unui flux dependent ar trebui să îi fie alocate resurse ori dacă toate celelalte 
fluxuri de care depinde sunt închise sau dacă nu este posibil să progreseze.

O greutate a fluxului este o valoarea între 1 și 256 și este specificat ca 
fluxuri cu același părinte **ar trebui** să aibă alocate resurse proporțional 
pe baza greutății lor.
