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
autorisent uniquement le protocole TCP ou UDP sont déployés entre les utilisateurs
et les serveurs qu’ils doivent atteindre. L'introduction d'un autre protocole de
transport provoque l'échec de N% des connexions car elles sont bloquées par des
boîtes ne la voyant pas comme étant UDP ou TCP et donc malfaisantes ou erronés
d'une manière ou d'une autre. Le taux d'échec de N% est souvent jugé trop élevé
pour en valoir la peine.

Additionally, changing things in the transport protocol layer of the network
stack typically means protocols implemented by operating system kernels.
Updating and deploying new operating system kernels is a slow process that
requires significant effort. Many TCP improvements standardized by the IETF
are not widely deployed or used because they are not broadly supported.

De plus, les modifications apportées à la couche de protocole de transport de la
stack réseau impliquent généralement des protocoles implémentés par les noyaux de
système d'exploitation. La mise à jour et le déploiement de nouveaux noyaux de
système d'exploitation est un processus lent qui nécessite des efforts importants.
De nombreuses améliorations TCP normalisées par l'IETF ne sont pas beaucoup
déployées ou utilisées car elles ne sont pas énormément prises en charge.

## Pourquoi pas SCTP sur UDP

SCTP is a reliable transport protocol with streams, and for WebRTC there are
even existing implementations using it over UDP.

This was not deemed good enough as a QUIC alternative due to several reasons,
including:

 - SCTP does not fix the head-of-line-blocking problem for streams
 - SCTP requires the number of streams to be decided at connection setup
 - SCTP does not have a solid TLS/security story
 - SCTP has a 4-way handshake, QUIC offers 0-RTT
 - QUIC is a bytestream like TCP, SCTP is message-based
 - QUIC connections can migrate between IP addresses but SCTP cannot

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
