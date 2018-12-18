# URLs HTTPS://

HTTP/3 sera exécuté en utilisant des URLs `HTTPS://`. Le monde est rempli de ces
URLs et il a été jugé peu pratique et tout à fait déraisonnable d'introduire un
autre schéma d'URL pour le nouveau protocole. Tout comme HTTP/2 n'a pas besoin d'un
nouveau schéma, HTTP/3 non plus.

La complexité supplémentaire de la situation de HTTP/3 réside toutefois dans le fait
que, lorsque HTTP/2 était un nouveau moyen de transporter HTTP sur le réseau, il
était toujours basé sur TLS et TCP comme l'était HTTP/1. Le fait que HTTP/3 soit
effectué sur QUIC change les choses en quelques aspects importants.

Les anciennes, en texte clair, URLs `HTTP://`, seront laissées telles quelles et,
au fur et à mesure que nous avançons dans le futur avec des transferts plus
sécurisés, elles seront probablement de moins en moins utilisées. Les requêtes
adressées à ces URLs ne seront tout simplement pas mises à niveau pour utiliser
HTTP/3. En réalité, ils passent rarement à HTTP/2 non plus, mais pour d'autres
raisons.

## Connexion initiale

La première connexion à un hôte récent, non visité précédemment pour une URL
HTTPS:// devra probablement être établie via TCP (éventuellement en plus d'une
tentative parallèle de connexion via QUIC). L'hôte peut être un ancien serveur sans
prise en charge de QUIC ou il peut y avoir une boîte intermédiaire entre les
obstacles empêchant le succès d'une connexion QUIC.

Un client et un serveur modernes négocieraient probablement HTTP/2 lors du premier
handshake. Lorsque la connexion a été configurée et que le serveur répond à une
requête HTTP du client, le serveur peut informer le client de sa prise en charge et
de sa préférence pour HTTP/3.
