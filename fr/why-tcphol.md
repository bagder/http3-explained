## Blocage de tête de ligne TCP

HTTP/2 est réalisé sur TCP et avec beaucoup moins de connexions TCP que lors de
l'utilisation de versions HTTP antérieures. TCP est un protocole pour des
transferts fiables et vous pouvez le considérer comme une chaîne imaginaire entre
deux machines. Ce qui est mis sur le réseau d'un côté finira par se retrouver à
l'autre bout, dans le même ordre - à terme. (Ou la connexion est rompue.)

![une chaîne TCP entre deux ordinateurs](../images/tcp-chain.png)

Avec HTTP/2, les navigateurs classiques effectuent des dizaines, voire des
centaines de transferts parallèles sur cette seule connexion TCP.

Si un seul paquet est abandonné ou perdu sur le réseau quelque part entre deux
terminaisons qui parlent HTTP/2, cela signifie que toute la connexion TCP est
interrompue et que le paquet perdu doit être retransmis et doit retrouver son
chemin jusqu'à la destination. Puisque TCP est cette "chaîne", cela signifie que si
un lien manque soudainement, tout ce qui viendrait après le lien perdu doit
attendre.

Illustration utilisant la métaphore de la chaîne lors de l'envoi de deux flux sur
cette connexion. Un flux rouge et un flux vert:

![la chaîne montrant des liens de différentes
couleurs](../images/tcp-chain-streams.png)

Cela devient un bloc de début de ligne basé sur TCP!

À mesure que le taux de perte de paquets augmente, HTTP/2 est de moins en moins
performant. Avec 2% de perte de paquets (ce qui est une qualité de réseau
épouvantable, remarquez-vous bien), des tests ont montré que les utilisateurs de
HTTP/1 sont généralement mieux lotis - car ils disposent généralement de six
connexions TCP pour répartir le paquet perdu donc pour chaque paquet perdu, les
autres connexions sans perte peuvent toujours continuer.

Résoudre ce problème n’est pas facile, et si tout de même possible, à faire avec
TCP.

## Les flux indépendants évitent le blocage

Avec QUIC, il existe toujours une connexion configurée entre les deux terminaisons
qui sécurise la connexion et la livraison des données.

![une chaîne QUIC entre deux ordinateurs](../images/tcp-chain.png)

Lors de la configuration de deux flux différents sur cette connexion, ils sont
traités indépendamment. Ainsi, si un lien manque à l'un des flux, seul ce flux,
cette chaîne particulière, doit s'interrompre et attend que le lien manquant soit
retransmis.

Illustré ici avec un flux jaune et un flux bleu envoyés entre deux terminaisons.

![deux flux QUIC entre deux ordinateurs](../images/quic-chain-streams.png)
