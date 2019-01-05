# Ossification

Internet est un réseau de réseaux. Il y a des équipements installés sur Internet
dans de nombreux endroits pour assurer le fonctionnement de ce réseau de réseaux.
Ces périphériques, les boîtiers distribués sur le réseau, sont ce que nous appelons
parfois des boîtiers centraux. Les zones situées quelque part entre les points
terminaisons sont l'une des deux parties principales impliquées dans un transfert
de données réseau traditionnel.

Ces boîtes servent à de nombreuses fins spécifiques, mais je pense que nous pouvons
dire qu'universellement, elles sont placées là parce que quelqu'un pense qu'elles
doivent être là pour que les choses fonctionnent.

Les boîtiers centraux routent les paquets IP entre les réseaux, bloquent le trafic
malveillant, effectuent la traduction d'adresses réseau (en anglais Network Address
Translation (NAT)), améliorent les performances, tentent parfois d'espionner le
trafic en passant, etc...

Afin de s'acquitter de leurs tâches, ces boîtiers doivent connaître la mise en
réseau et les protocoles qu'ils surveillent ou modifient. Ils exécutent des
logiciels à cette fin. Logiciels qui ne sont pas toujours mis à jour fréquemment.

Bien qu'ils soient des composants essentiels qui maintiennent Internet attaché, ils
ne sont pas souvent en phase avec les dernières technologies. Le milieu du réseau
ne se déplace généralement pas aussi vite que les bords, comme les clients et les
serveurs du monde.

Tous les protocoles de réseau que ces boîtes pourraient vouloir inspecter et qui
ont des idées sur ce qui est ok et ce qui ne l'est pas alors ont ce problème: ces
boîtes ont été déployées il y a quelque temps, alors que les protocoles avaient un
ensemble de fonctionnalités de cette époque. L'introduction de nouvelles
fonctionnalités ou de changements de comportement inconnus auparavant risquerait
d'être considérée comme mauvaise ou illégale par de telles boîtes. Ce trafic peut
tout simplement être supprimé ou retardé dans la mesure où les utilisateurs ne
souhaitent vraiment pas utiliser ces fonctionnalités.

C'est ce qu'on appelle "l'ossification du protocole".

Les modifications apportées au protocole TCP souffrent également d’ossification:
certaines boîtes entre un client et le serveur distant détectent de nouvelles
options TCP inconnues et bloquent ces connexions car ils ne savent pas quelles sont
les options. S'ils sont autorisés à détecter les détails de protocole, les systèmes
apprennent le comportement typique des protocoles et, avec le temps, il devient
impossible de les modifier.

Le seul moyen véritablement efficace de "combattre" l'ossification consiste à
chiffrer le plus possible la communication afin d'empêcher les boîtes moyennes de
voir beaucoup du protocole la traversant.
