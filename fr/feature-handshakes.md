# Handshakes rapides

QUIC offre à la fois des configurations de connexion 0-RTT et 1-RTT, ce qui
signifie qu'au mieux, QUIC ne nécessitera aucun aller-retour supplémentaire lors
de la configuration d'une nouvelle connexion. Le plus rapide des deux, la
négociation 0-RTT, ne fonctionne que si une connexion précédente a été établie
avec un hôte et qu'un secret de cette connexion a été mis en cache.

## Données précoces

QUIC permet à un client d'inclure des données déjà dans le handshake 0-RTT. Cette
fonctionnalité permet à un client de transmettre les données à l'homologue aussi
rapidement que possible, ce qui permet bien entendu au serveur de répondre et de
renvoyer les données encore plus tôt.
