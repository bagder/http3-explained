# Osificarea

Internetul este o rețea de rețele. Există dispozitive instalate pe internet în 
multe locuri diferite care se asigură că această rețea de rețele funcționează 
cum ar trebui. Aceste dispozitive, sisteme care sunt distribuite pe rețea, sunt 
ceea ce numim middlebox-uri - echipamente care sunt poziționate undeva între 
două sisteme și care sunt părțile principale implicate într-un transfer 
tradițional pe rețea.

Aceste echipamente servesc mai multe scopuri diferite, dar cred că putem spune 
cu siguranță că sunt puse acolo pentru că cineva crede că trebuie să fie acolo 
astfel încât lucrurile să funcționeze cum trebuie.

Middlebox-uri redirecționează pachete IP între rețele, blochează traficul 
răuvoitor, fac NAT (Network Address Translation - traducerea adreselor de rețea), 
îmbunătățesc performanța, unele încearcă să spioneze traficul care trece prin 
ele și așa mai departe.

Ca să își poată îndeplini sarcinile, aceste sisteme trebuie să aibă cunoștințe 
de rețelistică și despre protocoalele pe care trebuie să le monitorizeze sau să 
le modifice. Pentru acest scop, rulează aplicații software, iar aceste aplicații 
nu sunt mereu actualizate frecvent.

Chiar dacă sunt componente care fac internetul să funcționeze, de multe ori nu 
țin pasul cu ultimele tehnologii. Mijlocul rețelei, de obicei, nu se mișcă la 
fel de repede ca marginile - aplicațiile-client și server-le din lume.

Protocoalele de rețea pe care aceste echipamente ar vrea să le inspecteze și 
despre care ar vrea să stie dacă sunt OK sau nu au această problemă: aceste 
echipamente au fost publicate cu ceva timp în urmă, când protocoalele avea un 
set de caracteristici, valabil la acel moment. Introducerea unor noi 
funcționalități sau schimbări în comportament care nu erau cunoscute atunci sunt 
considerate rele sau interzise de aceste echipamente. Astfel de trafic poate fi 
oprit sau întârziat până la punctul în care utilizatorii nu își mai doresc să 
folosească funcționalitățile.

Asta se numește "osificarea protocoalelor".

Schimbările TCP "suferă", de asemenea, de osificare: unele echipamente între o 
aplicație-client și server o să identifice opțiuni noi TCP pe care nu o să le 
recunoscă și o să blocheze întreaga conexiune. Dacă le este permis să detecteze 
detalii legate de protocol, sistemele învață cum ar trebui să se comporte 
protocoalele de obicei și, cu timpul, devin imposibil de schimbat.

Singura metodă eficientă de a preveni osificarea este criptarea a unei bucăți 
cât mai mari din comunicare pe cât posibil, astfel încât middlebox-urile să nu 
poată vedea detalii ale protocoalelor care trec prin ele.
