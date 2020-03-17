# HTTP/3 spiegato

Lo slancio per scrivere questo libro è partito in Marzo 2018. Il piano consiste
nel documentare HTTP/3 e il protocollo sottostante, ossia QUIC. Perchè sono
stati concepiti, come funzionano, dettagli sul protocollo, implementazioni, etc.

Questo libro è inteso per essere libero, gratuito; consta dello sforzo condiviso
che include chiunque abbia voglia di contribuire.

## Prerequisiti

Al lettore di questo libro è richiesto di avere una comprensione basilare
di Reti TCP/IP, di HTTP e del mondo web. Per maggiori dettagli e specifiche
a proposito di HTTP/2 vi raccomandiamo di consultare preventivamente le
informazioni contenute su [http2 explained](https://daniel.haxx.se/http2/).

## L'autore

Il presente libro è stato ideato e scritto da [Daniel Stenberg
](https://daniel.haxx.se/). Daniel è fondatore e sviluppatore principale di
[curl](https://curl.haxx.se/), il client HTTP più usato al mondo.
Daniel ha lavorato con e per HTTP ed altri protocolli internet per più di
due decenni ed è l'autore di [http2 explained](https://daniel.haxx.se/http2/).

## Homepage

La homepage del libro si trova su [daniel.haxx.se/http3-explained
](https://daniel.haxx.se/http3-explained).

## Contribuire

Se dovessi trovare errori, omissioni o falsità in questo documento, perfavore
inviaci una versione aggiornata del paragrafo e ci assicureremo che la modifica
venga pubblicata. Attribuiremo il credito a chiunque si renda utile.
Spero di continuare a migliorare questo libro nel corso del tempo.

Preferibilmente, segnalare [errori](https://github.com/bagder/http3-explained/issues)
o [richieste pull](https://github.com/bagder/http3-explained/pulls) sulla pagina
GitHub del progetto.

## Licenze

Questo documento e tutti i suoi contenuti sono sottoposti a licenza
[Creative Commons Attribution 4.0 license](https://creativecommons.org/licenses/by/4.0/).
