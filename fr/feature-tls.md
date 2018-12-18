## TLS 1.3

La sécurité de transport utilisée dans QUIC utilise TLS 1.3 ([RFC
8446](https://tools.ietf.org/html/rfc8446)) et il n'y a jamais de connexions QUIC
non chiffrées.

TLS 1.3 présente plusieurs avantages par rapport aux anciennes versions de TLS,
mais l'une des principales raisons de son utilisation dans QUIC est que la 1.3 a
modifié le handshake pour exiger moins d'allers-retours. Cela réduit la latence du
protocole.

L'ancienne version de QUIC de Google utilisait une crypto personnalisée.
