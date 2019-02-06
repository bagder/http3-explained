## IETF

Il gruppo di lavoro QUIC, creato per standardizzare il protocollo all'interno
di IETF, decise che QUIC avrebbe dovuto essere in grado di veicolare altri
protocolli oltre il "semplice" HTTP. Il QUIC-Google si era finora occupato solo
di HTTP, più specificamente di frames HTTP/2, servendosi della sintassi gia 
disponibile per i frames HTTP/2.

Fu inoltre deciso che il QUIC-IETF dovesse basare il proprio framework di
sicurezza e cifratura sullo standard TLS 1.3 al posto delle modifiche "fatte in
casa" dal team Google.

Per soddisfare la volontà di veicolare "non solamente HTTP", l'architettura
QUIC di IETF fu separata in due livelli: il trasporto QUIC e la parte "HTTP
over QUIC" (riferendosi al suddetto livello utilizziamo anche il termine "hq").

Questa ultima separazione -innoqua quanto possa sembrare- ha creato sostanziose
differenze fra le versioni originali Google e la versione finale IETF.

Il gruppo di lavoro ha comunque deciso abbastanza presto di concentrarsi sulla
consegna -entro i termini preposti- della versione 1 di QUIC, ed ha quindi
prediletto lo sviluppo di HTTP, rinviando così lo sviluppo del trasporto
non-HTTP ad una seconda fase.

Quando abbiamo iniziato a lavorare allo sviluppo di questo libro nel Marzo 2018
l'idea era di consegnare le specifice di QUIC versione 1 verso Novembre 2018,
data finalmente riportata a Luglio 2019.

Mentre il lavoro della IETF è avanzato, il team Google ha integrato i dettagli
della nuova versione IETF ed ha iniziato ad avanzare progresivamente nella
direzione di ciò che potrebbe finalmente diventare lo standard IETF. Google ha
quindi continuato ad usare la propria versione di QUIC sia lato browser sia
lato server applicativi.

[Le più recenti implementazioni in via di sviluppo
](https://github.com/quicwg/base-drafts/wiki/Implementations) hanno deciso di
focalizzare gli sforzi in direzione della versione IETF ufficiale; non sono
perciò compatibili con le versioni proposte da Google.
