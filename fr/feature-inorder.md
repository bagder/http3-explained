## Livraison dans l'ordre

QUIC garantit la livraison des flux dans l'ordre, mais pas entre les flux. Cela
signifie que chaque flux enverra des données et maintiendra l’ordre des données,
mais chaque flux pourra atteindre la destination dans un ordre différent de celui
que l’application a envoyé!

Par exemple: les flux A et B sont transférés d'un serveur à un client. Le flux A
est démarré en premier, puis ensuite le flux B. Dans QUIC, un paquet perdu affecte
uniquement le flux auquel appartient le paquet perdu. Si le flux A perd un paquet
mais pas le flux B, le flux B peut poursuivre ses transferts et se terminer pendant
que le paquet perdu du flux A est retransmis. Ce n'était pas possible avec HTTP/2.

Illustré ici avec un flux jaune et un flux bleu envoyés entre deux points de
terminaison QUIC sur une seule connexion. Ils sont indépendants et peuvent arriver
dans un ordre différent, mais chaque flux est livré de manière fiable, dans l'ordre,
à l'application.

![deux flux QUIC entre deux ordinateurs](../images/quic-chain-streams.png)
