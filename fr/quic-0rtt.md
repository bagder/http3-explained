# 0-RTT

Pour réduire le temps nécessaire à l'établissement d'une nouvelle connexion, un
client déjà connecté à un serveur peut mettre en cache certains paramètres de cette
connexion et établir une connexion **0-RTT** avec le serveur. Cela permet au client
d'envoyer des données immédiatement, sans attendre la fin d'un handshake.
