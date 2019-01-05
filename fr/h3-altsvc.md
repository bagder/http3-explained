# Alt-svc

L'en-tête du service de remplacement (Alt-svc:) et sa trame `ALT-SVC` HTTP/2
correspondante ne sont pas créés spécifiquement pour QUIC ou HTTP/3. Ils font partie
d'un mécanisme déjà conçu et créé pour qu'un serveur indique à un client: "Regardez,
je lance le même service sur CET HÔTE en utilisant CE PROTOCOLE sur CE PORT" *. Voir
les détails dans la [RFC 7838](https://tools.ietf.org/html/rfc7838).

Un client qui reçoit une telle réponse Alt-svc est ensuite invité, s’il le prend en
charge et le souhaite, à se connecter en arrière-plan en parallèle à cet hôte
donné - à l’aide du protocole spécifié - et s’il réussit à basculer ses opérations
sur cela au lieu de la connexion initiale.

Si la connexion initiale utilise HTTP/2 ou même HTTP/1, le serveur peut répondre et
indiquer au client qu'il peut se reconnecter et essayer HTTP/3. Cela pourrait être
vers même hôte ou à un autre qui sait comment servir cette origine. Les informations
fournies dans une telle réponse Alt-svc ont un temporisateur d'expiration,
permettant aux clients de diriger les connexions et demandes ultérieures
directement vers l'hôte alternatif à l'aide du protocole alternatif suggéré,
pendant une certaine période.

## Exemple

Un serveur HTTP incluant une en-tête `Alt-Svc:` dans sa réponse:

    Alt-Svc: h3=":50781"

Cela indique que HTTP/3 est disponible sur le port UDP 50781 avec le même nom d'hôte
que celui utilisé pour obtenir cette réponse.

Un client peut ensuite essayer de configurer une connexion QUIC avec cette
destination et, en cas de succès, continuer à communiquer avec l’origine comme cela
au lieu de la version HTTP initiale.
