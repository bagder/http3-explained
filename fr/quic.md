# Comment QUIC fonctionne

Sans expliquer les bits et les octets exacts sur le réseau, cette section décrit le
fonctionnement des blocs de construction fondamentaux du protocole de transport
QUIC. Si vous souhaitez implémenter votre propre stack QUIC, cette description doit
vous donner une compréhension générale, mais pour tous les détails, référez-vous
aux actuel brouillons internets et RFCs de l'IETF.

1. Configurez une [connexion](quic-connections.md)
2. ... ce qui inclut la [sécurité TLS](quic-tls.md)
3. Puis utilisez [les flux](quic-streams.md)
