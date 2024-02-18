## Sécurisé

QUIC est toujours sécurisé. Il n'y a pas de version en texte clair du
protocole, donc négocier une connexion QUIC signifie faire de la cryptographie et
de la sécurité avec TLS 1.3. Comme mentionné ci-dessus, cela empêche l'ossification
ainsi que d'autres types de blocages et traitements spéciaux, et garantit que QUIC
possède toutes les propriétés sécurisées de HTTPS auxquelles les utilisateurs Web
s'attendent et souhaitent.

Il n’y a que quelques paquets handshake initiaux qui sont envoyés en clair, avant
que les protocoles de cryptage aient été négociés.
