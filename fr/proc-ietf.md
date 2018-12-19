## IETF

Le groupe de travail QUIC mis en place pour standardiser le protocole au sein de
l'IETF a rapidement décidé que le protocole QUIC devait pouvoir transférer des
protocoles autres que "simplement" HTTP. Google-QUIC ne transportait jamais que
HTTP - en pratique, il transportait ce qui était en réalité des trames HTTP/2, en
utilisant la syntaxe HTTP/2.

Il a également été indiqué que l'IETF-QUIC devrait baser son cryptage et sa
sécurité sur TLS 1.3 au lieu de l'approche "personnalisée" utilisée par Google-QUIC.

Afin de satisfaire la demande d'envoi-plus-que-HTTP, l'architecture de protocole
IETF QUIC a été scindée en deux couches distinctes: la couche de transport QUIC et
la couche "HTTP sur QUIC" (cette dernière parfois appelée "hq").

Cette division de couche, bien que cela puisse paraître inoffensif, a entraîné une
grande différence entre l'IETF-QUIC et l'original de Google-QUIC.

Cependant, le groupe de travail a rapidement décidé que pour se concentrer
correctement et délivrer la version 1 de QUIC à temps, il se concentrerait sur la
livraison de HTTP, laissant les transports non-HTTP à un travail ultérieur.

En mars 2018, lorsque nous avons commencé à travailler sur ce livre, le plan était
d'expédier la spécification finale de la version 1 de QUIC en novembre 2018; cela a
ensuite été reporté à juillet 2019.

Alors que les travaux sur l’IETF-QUIC ont progressé, l’équipe de Google a incorporé
les détails de la version de l’IETF et a commencé à faire progresser lentement sa
version du protocole vers ce que pourrait devenir la version de l’IETF. Google a
continué d'utiliser sa version de QUIC dans son navigateur et ses services.

[La plupart des nouvelles implémentations en cours de
développement](https://github.com/quicwg/base-drafts/wiki/Implementations)
ont décidé de se concentrer sur la version de l'IETF et ne sont pas compatibles
avec la version de Google.
