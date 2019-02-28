## Blocarea vârfului stivei în TCP

HTTP/2 este implementat peste TCP și folosește mult mai puține conexiuni
decât versiunile sale anterioare. TCP este un protocol pentru transferuri 
fiabile - vă puteți gândi la el ca la un lanț imaginar între două sisteme. Ce 
este trimis prin rețea de la un capăt va ajunge, eventual, la celălalt capăt.
Altfel, conexiunea va fi întreruptă.

![un lanț TCP între două computere](../images/tcp-chain.png)

Cu HTTP/2, browsere-le normale fac zeci sau sute de transferuri în paralel 
peste o singură conexiune TCP.

Dacă un singur pachet este ignorat, sau pierdut în rețea undeva între două 
componente care "vorbesc" HTTP/2, înseamnă că toată conexiunea TCP este oprită
până când pachetul pierdut este retransmis și își regăsește calea către 
destinatar. De vreme ce TCP este un "lanț", dacă o za a acestui lanț dispare
subit, tot ce vine după ea trebuie să aștepte.

O ilustrație care se folosește de metafora "lanțului" pentru a transmite două 
fluxuri, unul roșu și unul verde, printr-o singură conexiune:

![lanțul conținând zale în mai multe culori](../images/tcp-chain-streams.png)

Blocarea vârfului de stivă TCP:

Pe măsură ce rata de pierdere a pachetelor crește, HTTP/2 se mișcă din ce în ce
mai rău. La o pieredere de 2% (care reprezintă o calitate groaznică a rețelei),
testele au arătat că utilizatorii HTTP/1 sunt mai avantajați, deoarece au până
la 6 conexiune TCP deschise prin care se distribuie rata de pieredere a 
pachetelor. Asta înseamnă că, dacă o conexiune pierde un pachet, celelalte pot
continua.

O rezolvare a acestei probleme nu este ușoară sau, poate chiar posibilă, atunci
când se folosește TCP.

## Fluxurile independente evită blocarea

Atunci când este folosit QUIC, se face, de asemenea, o organizare a unei 
conexiuni între două sisteme, ceea ce face conexiunea să fie sigură și datele să
fie livrate fiabil.

![un lanț QUIC între două computere](../images/tcp-chain.png)

Două fluxuri separate trimise prin această conexiune sunt prelucrate independent,
astfel că, dacă o parte lipsește dintr-unul dintre fluxuri, numai acel flux și 
acel lanț trebuie să se oprească și să aștepte ca acea bucată să fie retrimisă.

Conceptul este ilustrat aici cu un flux galben și unul albastru, trimise între
două sisteme:

![două fluxuri QUIC între două sistee](../images/quic-chain-streams.png)
