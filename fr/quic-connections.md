# Connexions

Une connexion QUIC est une conversation unique entre deux terminaisons QUIC.
L’établissement de la connexion QUIC associe la négociation de la version à la
négociation cryptographique et du handshake de transfert afin de réduire le temps
d’attente de l’établissement de la connexion.

Pour envoyer des données via une telle connexion, un ou plusieurs flux doivent être
créés et utilisés.

## ID de connexion

Chaque connexion possède un ensemble d'identifiants de connexion, ou d'IDs de
connection, chacun d'entre eux pouvant être utilisé pour identifier la connexion.
Les IDs de connexion sont sélectionnés indépendamment par les terminaisons; chaque
terminaison sélectionne les identifiants de connexion que son pair utilise.

La fonction principale de ces IDs de connexion est de garantir que les changements
d’adressage au niveau des couches inférieures du protocole (UDP, IP et au-dessous)
n’entraînent pas la transmission des paquets d’une connexion QUIC à la mauvaise
terminaison.

En tirant parti de l'ID de connexion, les connexions peuvent ainsi migrer entre les
adresses IP et les interfaces réseau d'une manière que TCP n'aurais jamais pu. Par
exemple, la migration permet à un téléchargement en cours de passer d'une connexion
réseau cellulaire à une connexion wifi plus rapide lorsque l'utilisateur déplace
son appareil dans un emplacement proposant le wifi. De même, le téléchargement peut
s'effectuer par la connexion cellulaire si le wifi devient indisponible.

## Numéro de port

QUIC est construit sur UDP, donc un champ de numéro de port de 16 bits est utilisé
pour différencier les connexions entrantes.

## Négociation de version

Une demande de connexion QUIC émanant d'un client indiquera au serveur la version
du protocole QUIC qu'il souhaite utiliser, et le serveur répondra avec une liste
des versions prises en charge que le client pourra sélectionner.
