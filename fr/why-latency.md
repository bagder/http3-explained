# Données antérieures

QUIC offre à la fois des handshakes 0-RTT et 1-RTT qui réduisent le temps
nécessaire pour négocier et établir une nouvelle connexion. Comparez avec le
handshake à 3 voies du TCP.

En plus de ça, QUIC offre une prise en charge des "données antérieures" dès le
départ, ce qui est fait pour autoriser plus de données et est utilisé plus
facilement que TCP Fast Open.

Avec le concept de flux, vous pouvez établir une autre connexion logique avec le
même hôte sans avoir à d'abord attendre la fin de la connexion existante.

## TCP Fast Open est problématique

TCP Fast Open a été publié en décembre 2014 en tant que la [RFC
7413](https://tools.ietf.org/html/rfc7413) et cette spécification explique comment
les applications peuvent transmettre des données au serveur afin qu'elles soient
déjà livrées dans le premier paquet TCP SYN.

La prise en charge effective de cette fonctionnalité a pris du temps et pose encore
de nombreux problèmes, même aujourd'hui en 2018. Les responsables de la mise en
œuvre de la stack TCP ont rencontré des problèmes, tout comme les applications qui
ont essayé de tirer parti de cette fonctionnalité, en sachant dans quelle version
d'OS essayer pour l'activer mais également pour savoir comment revenir en arrière
avec élégance et régler les problèmes qui surviennent. Plusieurs réseaux ont été
identifiés pour interférer avec le trafic TFO et ont donc activement ruiné de
telles handshakes TCP.
