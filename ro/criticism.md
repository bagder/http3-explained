# Critici

## UDP nu va merge niciodată

Multe companii, operatori și organizații blochează sau limitează traficul UDP în 
afara port-ului 53 (folosit pentru DNS) din moment ce, în ultimul timp, a fost 
abuzat pentru atacuri. În mod special, câteva dintre protocoalele UDP existente 
și implementări de server populare pentru ele au fost vulnerabile la atacuri de 
amplificare, în care un atacator poate genera o cantitate mare de trafic de 
ieșire pentru a afecta victime nevinovate.

QUIC are o construită o temperare pentru atacurile de amplificare prin cererea 
ca pachetul inițial să fie de minim 1200 de octeți și printr-o regulă în 
protocol care spune că un server NU TREBUIE să trimită în răspuns mai mult de 
trei mărimea cererii, fără să fi primit un pachet de la client în răspuns.

## UDP este încet în kernel-uri

Asta pare a fi adevărat, cel puțin acum, în 2018. Nu putem, bineînțeles, să 
spunem cum se va dezvolta acest lucru și cât din asta este pur și simplu 
că rezultatul performanței transferurilor UDP nu a fost în prim plan pentru 
dezvoltatori de mulți ani.

Pentru majoritatea clienților, această "încetinire" nu va fi probabil observată 
vreodată.

## QUIC folosește prea multă capacitate de procesare

Similar cu remarca "UDP este încet" de deasupra, asta este parțial din cauză că 
folosirea TCP și TLS în lume a avut mult timp să se maturizeze, îmbunătățească 
și să primească asistență hardware.

Există motive să ne așteptăm că asta se îmbunătăți cu timpul. Întrebarea este 
cât de mult această capacitate de procesare în plus va afecta dezvoltatorii.

## Asta e numai Google

Nu, nu este. Google a adus specificația inițială la IETF după ce au demonstrat, 
la o scară largă pe internet, că publicarea acestui tip de protocol peste UDP 
chiar funcționează și are performanțe bune.

De atunci, persoane de la un număr mare de companii și organizații au lucrat în 
organizația neutră IETF să pună la punct un protocol de transport din ea. La 
acea muncă au participat, bineînțeles, și angajați Google, dar la fel au 
participat și angajați de la un număr mare de alte companii interesate în 
avansarea stării protocoalelor de transfer pe internet, inclusiz Mozilla, Fastly, 
Cloudfare, Akamai, Microsoft, Facebook și Apple.

## Asta e o îmbunătățire mult prea mică.

Asta nu este cu adevărat o critică, cât o opinie. Poate că este, și poate că 
este o îmbunătățire mult prea mică așa de aproape în timp de când a fost publicat 
HTTP/2.

HTTP/3 este probabil să funcționeze mult mai bine în rețele pline de pachete 
pierdute, oferă handshakes mai rapide, așa că va îmbunătăți timpii de încărcare 
atât percepuți cât și actuali. Dar este asta de ajuns ca benificii pentru a 
motiva oamenii să publice suport pentru HTTP/3 pe servere-le lor și pentru 
serviciile lor? Timpul și măsurătorile de perfomanță din viitor vor spune cu 
siguranță.
