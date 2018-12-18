# Spin Bit

Peut-être l'une des discussions de conception les plus longues au sein du groupe de
travail QUIC, qui a fait l'objet de plusieurs centaines de mails et d'heures de
discussions, concerne un seul bit: le Spin Bit.

Les partisans de ce bit insistent sur le fait qu'il est nécessaire que les
opérateurs et les personnes se trouvant entre deux terminaisons QUIC puissent
mesurer le temps de latence.

Les opposants à cette fonctionnalité n'aiment pas la potentielle fuite
d'informations.

## Faire tourner un bit

Les deux points de terminaison, le client et le serveur, conservent une valeur de
rotation, 0 ou 1, pour chaque connexion QUIC, et définissent le bit de rotation sur
les paquets qu'il envoie pour cette connexion sur la valeur appropriée.

Les deux côtés envoient ensuite des paquets avec ce bit de rotation défini sur la
même valeur pendant toute la durée d'un aller-retour, puis la valeur est modifiée.
L'effet est alors une impulsion de uns et de zéros dans ce champ binaire que les
observateurs peuvent surveiller.

Cette mesure ne fonctionne que lorsque l'expéditeur n'est ni limité par
l'application ni par le contrôle de flux, la réorganisation des paquets sur le
réseau peut également rendre les données tumultueuses.
