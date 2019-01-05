## ‎Plusieurs flux au sein de connexions

Semblable à SCTP, SSH et HTTP/2, QUIC propose des flux logiques séparés au sein des
connexions physiques. Un certain nombre de flux parallèles pouvant transférer des
données simultanément sur une seule connexion sans affecter les autres flux.

Une connexion est une configuration négociée entre deux points de terminaison,
similaire au fonctionnement d'une connexion TCP. Une connexion QUIC est établie sur
port UDP et une adresse IP, mais une fois établie, la connexion est associée à son
"ID de connexion".

Sur une connexion établie, chaque côté peut créer des flux et envoyer des données à
l'autre terminaison. Les flux sont livrés dans l'ordre et ils sont fiables, mais
différents flux peuvent être livrés dans le désordre.

QUIC offre un contrôle de flux sur la connexion et les flux.

Voir plus de détails dans les sections [connexion](quic-connections.md) et
[flux](quic-streams.md)
