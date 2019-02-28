# QUIC v2

Pentru a obține cel mai bun nivel de concentrare posibil pe miezul protocolului 
QUIC și pentru a putea livra la timp, câteva dintre funcționalitățile 
planificate inițial să fie parte din protocolul de bază au fost amânate și, 
acum, sunt planificate să fie gata într-o versiune QUIC ulterioară. Versiunea 
QUIC 2 sau mai mare.

Autorul acestui document deține, totuși, un glob de cristal relativ stricat, așa 
că nu putem spune sigur exact ce funcționalități vor apărea sau nu în versiunea 
2. Putem, totuși să menționăm câteva dintre funcționalitățile și lucrurile care 
au fost scoase explicit din versiunea 1 a muncii pentru a fi "lucrate mai 
târziu" și care e posibil să apară într-o versiune 2.

## Forward Error Correction

Forward error correction (FEC) este o metodă de a obține control asupra erorilor 
în transmisiuni în care emițătorul trimite informații redundante, iar receptorul 
recunoaște numai o bucată din informația care nu conține, aparent, nicio eroare.

Google a experimentat cu asta în munca lor originală asupra QUIC, dar, ulterior, 
a înlăturat-o din nou, de vreme ce experimentele nu au ieșit atât de bine. 
Această funcționalitate este supusă discuției pentru QUIC v2, dar, probabil, va 
dura mult până când cineva va dovedi că este o adiție folositoare, fără prea 
multe penalizări.

## Multipath

Multipath înseamnă că transferul poate, în sine, folosi mai multe rute de rețea 
pentru a maximiza folosirea resurselor și creșterea redundanței.

Apărătorii SCTP din lume doresc să menționeze că SCTP deja include multipath, la 
fel ca și TCP modern.

## Informații inconsistente

A fost discutată oferirea ca opțiune de fluxuri "inconsistente", ceea ce ar 
permite QUIC să înlocuiască și programele stil-UDP.

## Adaptări non-HTTP

DNS peste QUIC a fost una dintre mențiunile de protocoale non-HTTP timpurii, 
care ar putea primi niște atenție odată ce versiunea 1 a QUIC și HTTP/3 sunt 
lansate. Dar cu un nou transfer ca acesta oferit lumii, nu îmi pot imagina că se 
va opri acolo
