# API

L’un des facteurs de succès du TCP classique et des programmes qui l’utilisent est
l’API de socket standardisé. Il a des fonctionnalités bien définies et à l'aide de
cette API, vous pouvez déplacer des programmes entre de nombreux systèmes
d'exploitation différents, car TCP fonctionne de la même manière.

QUIC n'est pas là. Il n'y a pas d'API standard pour QUIC.

Avec QUIC, vous devez choisir l’une des implémentations de bibliothèque existantes
et s'en tenir à son API. Cela rend les applications "verrouillées" à une
seule bibliothèque dans une certaine mesure. Le passage à une autre bibliothèque
signifie une autre API, ce qui peut nécessiter beaucoup de travail.

De plus, étant donné que QUIC est généralement implémenté dans l'espace utilisateur,
il ne peut pas simplement enrichir l'API de socket ou sembler similaire à la
fonctionnalité existante des protocoles TCP et UDP. L'utilisation de QUIC signifie
l'utilisation d'une autre API que l'API socket.
