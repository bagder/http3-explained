## Vous vous souvenez d'HTTP/2 ?

La spécification HTTP/2 [RFC 7540](https://httpwg.org/specs/rfc7540.html) a été
publiée en mai 2015 et le protocole a depuis été mis en œuvre et déployé largement
sur Internet et sur le World Wide Web.

Début 2018, près de 40% des 1 000 meilleurs sites Web utilisaient HTTP/2, environ
70% de toutes les demandes HTTPS de Firefox recevaient des réponses HTTP/2 et tous
les principaux navigateurs, serveurs et proxies le prenaient en charge.

HTTP/2 corrige toute une série de lacunes presentes dans HTTP/1 et avec
l'introduction de la deuxième version de HTTP, les utilisateurs peuvent cesser
d'utiliser toute une série de solutions de contournement. Certaines sont assez
pénibles pour les développeurs Web.

L'une des principales caractéristiques de HTTP/2 est qu'il utilise le multiplexage,
de sorte que de nombreux flux logiques soient envoyés sur la même connexion TCP
physique. Cela rend beaucoup de choses meilleures et plus rapides. Le contrôle de
congestion fonctionne bien mieux, il permet aux utilisateurs d’utiliser bien mieux
le protocole TCP et ainsi de saturer correctement la bande passante, de rendre les
connexions TCP plus durables - ce qui est bien pour qu’ils atteignent la vitesse
maximale plus souvent qu’avant. La compression d'en-tête lui fait utiliser moins de
bande passante.

Avec HTTP/2, les navigateurs utilisent généralement *une* connexion TCP avec chaque
hôte au lieu des précédents *six*. En fait, les techniques de fusion et de
"désarchivage" des connexions utilisées avec HTTP/2 peuvent même réduire beaucoup
plus que ça le nombre de connexions.

HTTP/2 a corrigé le problème de blocage de tête de ligne HTTP, dans lequel les
clients devaient attendre la fin de la première requête en ligne avant que la
suivante ne puisse être envoyée.

![http2 man](../images/h2-man.jpg)
