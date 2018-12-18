# QUIC v2

Afin de se concentrer au mieux sur le coeur du protocole QUIC et de pouvoir le
livrer à temps, plusieurs fonctionnalités qui étaient prévues à l'origine pour
faire partie du protocole principal ont été reportées et sont maintenant prévues
pour être remplacées dans une prochaine version de QUIC. QUIC version 2 ou au-delà.

Cependant, l’auteur de ce document a une boule de cristal plutôt défectueuse, nous
ne pouvons donc pas savoir exactement quelles fonctionnalités apparaîtront ou ne
figureront pas dans la version 2. Nous pouvons toutefois mentionner certaines des
fonctionnalités et éléments explicitement supprimés du travail de la v1 pour être
"travaillé plus tard" et pourraient alors éventuellement apparaître dans une 
version 2.

## Forward Error Correction

La Correction d'Erreur Directe (en englais Forward Error Correction (FEC)) est une
méthode d'obtention du contrôle d'erreur dans la transmission de données dans
laquelle l'émetteur envoie des données redondantes et le récepteur ne reconnaît que
la partie des données qui ne contient aucune erreur apparente.

FEC a été expérimenté par Google dans leur travail original sur QUIC, mais
il a été retiré à nouveau car les expériences ne se sont pas bien déroulées.
Cette fonctionnalité est un sujet de discussion pour QUIC v2, mais il faut
probablement que quelqu'un prouve qu’elle peut en fait être un ajout utile sans
pénalité excessive.

## Multitrajet

Multitrajet (en anglais multipath) signifie que le transport peut lui-même utiliser
plusieurs chemins d'accès réseau pour optimiser l'utilisation des ressources et
augmenter la redondance.

Les partisans du SCTP dans le monde aiment mentionner que le SCTP est déjà
multitrajet, tout comme le TCP moderne.

## Données non fiables

Il a été envisagé de proposer comme option des flux "non fiables", qui permettraient alors à QUIC de remplacer également les applications de type UDP.

## Adaptations non-HTTP

DNS sur QUIC est l’un des premiers protocoles non HTTP mentionnés qui pourrait attirer l’attention une fois que QUIC v1 et HTTP/3 seront disponibles. Mais avec un nouveau moyen de transport comme celui-ci ayant été apporté au monde, je ne peux pas imaginer que cela s’arrêtera là.
