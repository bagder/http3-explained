# Flux

Les flux dans QUIC fournissent une abstraction légère, ordonnée et ordonnée.

Il existe deux types de flux de base dans QUIC:

  - Les flux unidirectionnels transportent des données dans un sens: de
    l'initiateur du flux à son homologue.

  - Les flux bidirectionnels permettent l'envoi de données dans les deux sens.

L'un ou l'autre type de flux peut être créé par l'un ou l'autre des points de
terminaison, peut simultanément envoyer des données entrelacées à d'autres flux et
peut être annulé.

Pour envoyer des données via une connexion QUIC, un ou plusieurs flux sont utilisés.

## Contrôle de flux

Streams are individually flow controlled, allowing an endpoint to limit memory
commitment and to apply back pressure. The creation of streams is also flow
controlled, with each peer declaring the maximum stream ID it is willing to
accept at a given time.

Les flux sont contrôlés individuellement, ce qui permet à un point de terminaison
de limiter l’engagement de la mémoire et d’appliquer une contre-pression. La
création de flux est également contrôlée en flux, chaque pair déclarant l’ID de
flux maximum qu’il est prêt à accepter à un moment donné.

## Identificateurs de flux

Les flux sont identifiés par un entier non signé de 62 bits, appelé ID de flux. Les
deux bits les moins significatifs de l'ID de flux sont utilisés pour identifier le
type de flux (unidirectionnel ou bidirectionnel) et l'initiateur du flux.

Le bit le moins significatif (0x1) de l'ID de flux identifie l'initiateur du flux.
Les clients initient des flux pairs (ceux dont le bit le moins significatif est
défini sur 0); les serveurs lancent des flux impairs (avec le bit mis à 1).

Le deuxième bit le moins significatif (0x2) de l'ID de flux différencie les flux
unidirectionnels des flux bidirectionnels. Les flux unidirectionnels ont toujours
ce bit défini sur 1 et les flux bidirectionnels ont ce bit défini sur 0.

## Flux simultané

QUIC permet à un nombre arbitraire de flux de fonctionner simultanément. Une
terminaison limite le nombre de flux entrants actifs simultanément en limitant l'ID
de flux maximal.

L'ID de flux maximal est spécifique à chaque terminaison et s'applique uniquement à
l'homologue qui reçoit le paramètre.

## Envoi et réception de données

Les terminaisons utilisent des flux pour envoyer et recevoir des données. C'est
après tout leur but ultime. Les flux sont une abstraction ordonnée de flux
d'octets. Les flux séparés ne sont toutefois pas nécessairement livrés dans l'ordre
d'origine.

## Priorité des flux

Le multiplexage de flux a un effet significatif sur les performances des
applications si les ressources allouées aux flux sont correctement hiérarchisées.
L'expérience acquise avec d'autres protocoles multiplexés, tels que HTTP/2, montre
que des stratégies efficaces de hiérarchisation ont un impact positif significatif
sur les performances.

QUIC lui-même ne fournit pas de frames pour l'échange d'informations sur la
priorisation. Au lieu de cela, il repose sur la réception d'informations de
priorité de l'application qui utilise QUIC. Les protocoles qui utilisent QUIC
peuvent définir n’importe quel schéma de priorisation adapté à la sémantique de
leurs applications.

Lorsque HTTP/3 est utilisé sur QUIC, la hiérarchisation est effectuée dans la
couche HTTP.
