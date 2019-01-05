## Espace utilisateur

L'implémentation d'un protocole de transport dans l'espace utilisateur permet une
itération rapide du protocole, car il est relativement facile de faire évoluer le
protocole sans nécessiter que les clients et les serveurs mettent à jour le noyau
de leur système d'exploitation pour déployer de nouvelles versions.

Rien d’inhérent dans QUIC ne l’empêche d’être implémenté et proposé ultérieurement
par les noyaux de systèmes d’exploitation, si quelqu'un trouve ça une bonne idée.

### De nombreuses implémentations

Un des effets évidents de l’implémentation d’un nouveau protocole de transport dans
l’espace utilisateur est que nous pouvons nous attendre à de nombreuses
implémentations indépendantes.

Différentes applications sont susceptibles d'inclure (ou de superposer) différentes
implémentations de HTTP/3 et de QUIC dans un avenir prévisible.
