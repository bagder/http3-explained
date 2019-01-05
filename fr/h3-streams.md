# Flux QUIC et HTTP/3

HTTP/3 étant conçu pour QUIC, il tire pleinement parti des flux de QUIC, où HTTP/2
devait concevoir l'ensemble de son concept de flux et de multiplexage au-dessus de
TCP.

Les requêtes HTTP effectuées via HTTP/3 utilisent un ensemble spécifique de flux.

## Trames HTTP/3

HTTP/3 signifie la configuration de flux QUIC et l’envoi d’un ensemble de trames à
l’autre extrémité. Il n'y a qu'un petit nombre fixe (huit!) de trames connues dans
HTTP/3. Les plus importants sont probablement:

- HEADERS, qui envoie des en-têtes HTTP compressés
- DATA, envoie le contenu des données binaires
- GOAWAY, veuillez arrêter cette connexion

## Requête HTTP

Le client envoie sa requête HTTP sur un flux QUIC *bidirectionnel* initié par le
client.

Une requête consiste en une seule trame HEADERS et peut éventuellement être suivie
d'une ou deux autres trames: une série de trames DATA et éventuellement d'une trame
HEADERS finale pour terminer.

Après avoir envoyé une requête, un client ferme le flux pour l’envoyer.

## Réponse HTTP

Le serveur renvoie sa réponse HTTP sur le flux bidirectionnel. Une trame HEADERS,
une série de trames DATA et éventuellement une dernière trame HEADERS.

## En-têtes QPACK

Les trames HEADERS contiennent des en-têtes HTTP compressés à l'aide de
l'algorithme QPACK, QPACK est styliquement similaire à celui de la compression
HTTP/2 appelée HPACK ([RFC 7541](https://httpwg.org/specs/rfc7541.html)), mais
modifiée pour fonctionner avec des flux livrés dans le désordre.

QPACK lui-même utilise deux flux QUIC unidirectionnels supplémentaires entre les
deux terminaisons. Ils sont utilisés pour transporter des informations de table
dynamique dans les deux sens.
