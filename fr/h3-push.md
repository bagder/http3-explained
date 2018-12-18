# HTTP/3 push serveur

Un serveur push HTTP/3 est similaire à ce qui est décrit dans HTTP/2 ([RFC
7540](https://httpwg.org/specs/rfc7540.html)), mais utilise des mécanismes
différents.

Un serveur push est en réalité la réponse à une requête que le client n'a jamais
envoyée!

Les push serveur ne sont autorisés que si le côté client les a acceptés. Dans
HTTP/3, le client définit même une limite pour le nombre de push qu'il accepte en
informant le serveur de l'ID de flux de push maximal. Dépasser cette limite
entraînera une erreur de connexion.

Si le serveur estime probable que le client souhaite une ressource supplémentaire
qu'il n'a pas demandée mais qu'il devrait avoir de toute façon, il peut envoyer une
trame `PUSH_PROMISE` (sur le flux de la requête) indiquant à quoi ressemble la
requête dont la réponse est destinée, puis envoyer cette réponse réelle sur un
nouveau flux.

Même si les envois ont au préalable été déclarés acceptables par le client, chaque
flux envoyé individuellement peut toujours être annulé à tout moment si le client
le juge approprié. Il envoie ensuite une trame `CANCEL_PUSH` au serveur.

## Problématique

Depuis que cette fonctionnalité a été abordée pour la première fois dans le
développement de HTTP/2 et ensuite plus tard, après que le protocole ai été livré
et déployé sur Internet, cette fonctionnalité a été discutée, détestée et
perfectionnée de nombreuses différentes manières afin de la rendre utile.

Un envoi n’est jamais "gratuit", car même s’il enregistre un demi aller-retour, il
utilise toujours de la bande passante. Il est souvent difficile ou impossible pour
le côté serveur de savoir avec un niveau élevé de certitude si une ressource doit
être envoyée ou non.
