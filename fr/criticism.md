# Critique

## UDP ne fonctionnera jamais

Beaucoup d'entreprises, d'opérateurs et d'organisations bloquent ou limitent
le débit du traffic UDP en dehors du port 53 (utilisé pour DNS) depuis qu'il a
été depuis ces derniers jours principalement abusé pour des attaques. En 
particulier, certains des protocoles UDP existants et leur implémentations
populaires pour serveur ont été vulnérables aux attaques par amplification
dans lesquelles un attaquant peut générer une quantité considérable de trafic
sortant afin de cibler des victimes innocentes.

QUIC dispose d’une atténuation intégrée contre les attaques d’amplification en
exigeant que le paquet initial soit au minimum de 1200 octets et par une
restriction dans le protocole qui stipule qu’un serveur NE DOIT PAS envoyer
plus de trois fois la taille de la requête en réponse sans recevoir un paquet
du client en réponse.

## UDP est lent dans les noyaux

Cela semble être la vérité, du moins aujourd'hui en 2018. Nous ne pouvons
bien sûr pas dire comment cela va évoluer et à quel point cela est simplement
le résultat des performances de transfert UDP qui ne sont plus au cœur des
préoccupations des développeurs depuis de nombreuses années.

Pour la plupart des clients, cette "lenteur" n’est probablement même jamais
perceptible.

## QUIC prend trop de processeur

Semblable à remarque "UDP est lent" ci-dessus, c'est en partie du fait que
l'utilisation du protocole TCP et TLS dans le monde a pris plus de temps pour se
développer, s'améliorer et obtenir une assistance matérielle.

Il y a des raisons de s'attendre à ce que cela s'améliore avec le temps. La
question est de savoir de combien et combien cette utilisation supplémentaire du
processeur va faire mal aux déployeurs.

## C'est juste Google

Non ça ne l'est pas. Google a communiqué les spécifications initiales à l'IETF
après avoir prouvé, à grande échelle à l'échelle de l'Internet, que le
déploiement de ce style de protocole sur UDP fonctionne actuellement et
correctement.

Depuis lors, des membres d’un grand nombre d’entreprises et d’organisations ont
travaillé au sein de l’organisation indépendante du fournisseur, l’IETF, pour
élaborer un protocole de transport standard. Les employés de Google y ont bien
sûr participé, tout comme les employés d’un grand nombre d’autres entreprises
intéressées par l’état des protocoles de transport sur Internet, notamment
Mozilla, Fastly, Cloudflare, Akamai, Microsoft, Facebook et Microsoft. Apple.

## C'est une trop petite amélioration

Ce n'est pas vraiment une critique mais une opinion. Peut-être est-ce le cas, et
c’est peut-être une amélioration trop minime, trop proche dans le temps depuis
la publication de HTTP/2.

HTTP/3 fonctionnera probablement beaucoup mieux dans les réseaux saturés de
pertes de paquets, il offre des handshakes plus rapide, ce qui améliore la
latence réelle et perçue. Mais est-ce assez d'avantages pour motiver les gens à
déployer la prise en charge HTTP/3 sur leurs serveurs et pour leurs services? Le
temps et les mesures de performance futures nous le diront sûrement!
