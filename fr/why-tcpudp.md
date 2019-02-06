## TCP ou UDP

Si nous ne pouvons pas résoudre le blocage de la tête de ligne dans TCP, nous
devrions théoriquement pouvoir créer un nouveau protocole de transport à côté de
UDP et TCP dans la stack réseau. Ou peut-être même utilisez-vous
[SCTP](https://en.wikipedia.org/wiki/Stream_Control_Transmission_Protocol) qui est
un protocole de transport normalisé par l'IETF dans la [RFC
4960](https://tools.ietf.org/html/rfc4960) avec plusieurs des caractéristiques
souhaitées.

Cependant, au cours des dernières années, les efforts pour créer de nouveaux
protocoles de transport ont été presque complètement arrêtés en raison de la
difficulté de les déployer sur Internet. Le déploiement de nouveaux protocoles est
entravé par de nombreux pare-feu, NATs, routeurs et autres boîtes centrales qui
autorisent uniquement le protocole TCP ou UDP déployés entre les utilisateurs
et les serveurs qu’ils doivent atteindre. L'introduction d'un autre protocole de
transport provoque l'échec de N% des connexions car elles sont bloquées par des
boîtes ne la voyant pas comme étant UDP ou TCP et donc malfaisantes ou erronés
d'une manière ou d'une autre. Le taux d'échec de N% est souvent jugé trop élevé
pour en valoir la peine.

De plus, les modifications apportées à la couche de protocole de transport de la
stack réseau impliquent généralement des protocoles implémentés par les noyaux de
système d'exploitation. La mise à jour et le déploiement de nouveaux noyaux de
système d'exploitation est un processus lent qui nécessite des efforts importants.
De nombreuses améliorations TCP normalisées par l'IETF ne sont pas beaucoup
déployées ou utilisées car elles ne sont pas énormément prises en charge.

## Pourquoi pas SCTP sur UDP

SCTP est un protocole de transport fiable avec des flux, et pour WebRTC, il existe
même des implémentations existantes qui l'utilisent via UDP.

Cela n’a pas été jugé suffisant comme alternative à QUIC pour plusieurs raisons,
notamment:

 - SCTP ne résout pas le problème de blocage de tête de ligne pour les flux
 - SCTP exige que le nombre de flux soit déterminé lors de l'établissement de la
   connexion
 - SCTP n'a pas un solide concept TLS/de sécurité
 - SCTP a un handshake à 4 voies, QUIC offre 0-RTT
 - QUIC est un flux par octet comme TCP, SCTP est basé sur des messages
 - Les connexions QUIC peuvent migrer entre les adresses IP, mais SCTP ne peut pas

Pour plus de détails sur les différences, voir [A Comparison between SCTP and
QUIC](https://tools.ietf.org/html/draft-joseph-quic-comparison-quic-sctp-00).
