# Connections use TLS

Immédiatement après le paquet initial établissant une connexion, l'initiateur envoie
une trame de cryptage qui commence à établir le handshake de couche sécurisée. La
couche de sécurité utilise la sécurité TLS 1.3.

Il n'y a aucun moyen de vous désabonner ou d'éviter d'utiliser TLS pour une
connexion QUIC. Le protocole est conçu pour être difficile à altérer par des boîtes
intermédiaires, afin de prévenir l'ossification du protocole.
