## Protocole de transfert sur UDP

QUIC est un protocole de transfert implémenté au-dessus d'UDP. Si vous surveillez
votre trafic réseau par hasard, vous verrez QUIC apparaître sous forme de paquets
UDP.

Basé sur UDP, il utilise également les numéros de port UDP pour identifier des
serveurs spécifiques sur une machine donnée.

Toutes les implémentations QUIC connues se trouvent actuellement dans l'espace
utilisateur, ce qui permet une évolution plus rapide que ne permettent
généralement pas les implémentations noyau.

## Est-ce que ça va fonctionner ?

Certaines entreprises et autres configurations réseau bloquent le trafic UDP sur
des ports autres que 53 (utilisé pour DNS). D'autres limitent ces données de
manière à rendre QUIC moins performant que les protocoles basés sur TCP. Il n'y a
pas de fin à ce que certains opérateurs peuvent faire.

Dans un avenir prévisible, toute utilisation de transports basés sur QUIC devra
probablement être en mesure de faire appel à une autre alternative (basée sur TCP).
Les ingénieurs de Google ont précédemment mentionné les taux d'échec mesurés dans
de faibles pourcentages à un chiffre.

## Cela va-t-il s'améliorer ?

Il est fort probable que si QUIC s'avère être un atout précieux au monde d'Internet,
les utilisateurs voudront l'utiliser et le feront fonctionner dans leurs réseaux, ce
qui permettra aux entreprises de reconsidérer leurs obstacles. Au fil des années, le
développement de QUIC a progressé, le taux de réussite de l’établissement et de
l’utilisation de connexions QUIC sur Internet a augmenté.
