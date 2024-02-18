## Niveau de transport et d'application

Le protocole IETF QUIC est un protocole de transport sur lequel d'autres protocoles
d'application peuvent être utilisés. Le protocole de couche d'application initial
est HTTP/3 (h3).

La couche de transport prend en charge les connexions et les flux.

L'ancienne version de QUIC de Google regroupait le transport et le protocole HTTP
dans un même ensemble et constituait un protocole send-http/2-frames-over-udp plus
spécifique.
