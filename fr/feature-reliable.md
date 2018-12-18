## Transferts de données fiables

Bien qu'UDP ne soit pas un transport fiable, QUIC ajoute une couche au-dessus d'UDP
qui introduit la fiabilité. Il offre la retransmission de paquets, le contrôle de
congestion, la stimulation et les autres fonctionnalités présentes par ailleurs
dans TCP.

Les données envoyées sur QUIC depuis un point de terminaison apparaîtront dans
l'autre tôt ou tard, tant que la connexion est maintenue.
