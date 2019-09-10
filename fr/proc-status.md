# Statut

Le groupe de travail de QUIC a travaillé d'arrache-pied depuis fin 2016 pour
spécifier les protocoles et le plan est maintenant de le faire d'ici juillet 2019.

En novembre 2018, il n'y avait toujours pas de tests d'interopérabilité plus grands
avec HTTP/3 - uniquement avec les deux implémentations existantes et aucun d'entre
eux n'est effectué par un navigateur ou un logiciel populaire de serveur ouvert.

Il y a une quinzaine de [différentes implémentations de QUIC
répertoriées](https://github.com/curl/curl/wiki/QUIC-implementation) dans les pages
de wiki des groupes de travail de QUIC, mais toutes ne peuvent pas interagir sur
les dernières revisions des spécifications.

L'implémentation de QUIC n'est pas facile et le protocole a continué à évoluer,
même à cette date.

## Les serveurs

Le support NGINX pour QUIC et HTTP/3 est en cours de développement.
Il est prévu qu'il soit déployé durant le 
[cycle de développement NGINX 1.17](https://trac.nginx.org/nginx/milestone/nginx-1.17).

Il n'y a eu aucune déclaration publique en termes de support QUIC d'Apache.

## Les clients

Aucun des plus gros éditeurs de navigateurs n’a encore fourni de version, quel que
soit son état, pouvant exécuter la version IETF de QUIC ou de HTTP/3.

Google Chrome est livré avec une implémentation fonctionnelle de la version QUIC de
Google depuis de nombreuses années, mais cela n'interagit pas avec le protocole
QUIC officiel et son implémentation HTTP est différente de HTTP/3.

Mozilla est en train de développer [Neqo](https://github.com/mozilla/neqo/) - une
implémentation de QUIC et HTTP/3 écrit en [Rust](https://www.rust-lang.org/).
Neqo est [prévu d'être intégré](https://github.com/mozilla/neqo/issues/10) dans
[Necko](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/Necko) (qui est une 
biliothèque réseau utilisé dans plein d'applications clientes basés sur Mozilla - 
Firefox inclus).

## Obstacles d'Implémentation

QUIC a décidé d'utiliser TLS 1.3 comme base pour la couche de chiffrement et de
sécurité pour éviter d'inventer quelque chose de nouveau et plutôt s'appuyer sur un
protocole fiable et existant. Cependant, ce faisant, le groupe de travail a
également décidé que, pour rationaliser réellement l'utilisation de TLS dans QUIC,
il ne devrait utiliser que des "messages TLS" et non des "enregistrements TLS" pour
le protocole.

Cela peut sembler être un changement anodin, mais cela a en fait créé un obstacle
considérable pour de nombreux développeurs de stack QUIC. Les bibliothèques TLS
existantes qui prennent en charge TLS 1.3 n'ont tout simplement pas assez d'API
pour exposer cette fonctionnalité et permettre à QUIC d'y accéder. Bien que
plusieurs développeurs QUIC proviennent de grandes organisations qui travaillent
sur leur propre stack TLS en parallèle, cela n’est pas vrai pour tout le monde.

OpenSSL, le poids lourd open source dominant, par exemple, n’a pas d’API et n’a
manifesté aucun désir de la fournir dans les meilleurs délais (à partir de novembre
2018).

Cela entraînera éventuellement des obstacles de déploiement puisque les stacks QUIC
devront se baser sur d'autres bibliothèques TLS, utiliser une version OpenSSL
corrigée ou nécessiter une mise à jour d'une version future d'OpenSSL.

## Noyaux et charge du processeur

Google et Facebook ont tous deux mentionné que leurs déploiements à grande échelle
de QUIC requièrent environ deux fois plus de ressources processeur que la même
charge de trafic lorsque HTTP/2 est utilisé via TLS.

Quelques explications à cela incluent

- Les composants UDP, principalement sous Linux, ne sont pas du tout aussi optimisés
  que la stack TCP, car elle n’a pas été utilisée traditionnellement pour des
  transferts à grande vitesse comme celui-ci.

- Le déchargement TCP et TLS sur le matériel existe, mais cela est beaucoup plus
  rare pour UDP et pratiquement inexistant pour QUIC.

Il y a des raisons de croire que les performances et les exigences en matière de
processeur s'amélioreront avec le temps.
