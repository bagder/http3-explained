# Priorisation de HTTP/3

Une des trames de flux HTTP/3 s'appelle `PRIORITY`. Elle est utilisée pour définir
la priorité et la dépendance à un flux d'une manière similaire à celle de HTTP/2.

La trame peut définir un flux spécifique pour dépendre d'un autre flux spécifique
et définir un "poids" sur un flux donné.

Des ressources dépendantes doivent se voir allouer des ressources que si tous les
flux dont il dépend sont fermés ou s'il est impossible de progresser sur ces flux.

Un poids de flux est compris entre 1 et 256 et il est spécifié que les flux avec le
même parent **devraient** se voir allouer des ressources proportionnellement en
fonction de leur poids.
