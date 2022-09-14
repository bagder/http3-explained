## IETF

El grupo de trabajo de QUIC que se creó para estandarizar el protocolo dentro de
la IETF decidió rápidamente que el protocolo QUIC debía ser capaz de transferir
otros protocolos además de "sólo" HTTP. Google-QUIC sólo transportaba HTTP - 
en la práctica transportaba lo que era efectivamente tramas HTTP/2, utilizando 
la sintaxis de tramas HTTP/2.

También se afirmó que el IETF-QUIC debería basar su cifrado y seguridad en TLS
1.3 en lugar del enfoque "personalizado" utilizado por Google-QUIC.

Con el fin de satisfacer la demanda de enviar-más-que-sólo-HTTP, la arquitectura
del protocolo IETF-QUIC se dividió en dos capas separadas: el transporte QUIC y
la capa "HTTP sobre QUIC" - esta última fue renombrada como HTTP/3 en noviembre
de 2018.

Esta división de capas, aunque pueda parecer inocua, ha hecho que el IETF-QUIC
difiera bastante del Google-QUIC original.

Sin embargo, el grupo de trabajo pronto decidió que para conseguir el enfoque
adecuado y la capacidad de entregar la versión 1 de QUIC a tiempo, se centraría
en entregar HTTP, dejando los transportes no HTTP para un trabajo posterior.

En marzo de 2018, cuando comenzamos a trabajar en este libro, el plan era enviar
la especificación final para la versión 1 de QUIC en noviembre de 2018, pero
esto se ha pospuesto varias veces y, en el momento de escribir este artículo 
(junio de 2020), está entrando en las etapas finales.

Mientras el trabajo en IETF-QUIC ha progresado, el equipo de Google ha 
incorporado detalles de la versión del IETF y ha comenzado a progresar
lentamente su versión del protocolo hacia lo que la versión del IETF podría 
llegar a ser. Google ha seguido utilizando su versión de QUIC en su navegador y
sus servicios.

[La mayoría de las nuevas implementaciones en 
desarrollo](https://github.com/quicwg/base-drafts/wiki/Implementations) han 
decidido centrarse en la versión del IETF y no son compatibles con la versión de
Google.
