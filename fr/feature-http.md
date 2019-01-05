## HTTP/3

La couche HTTP effectue des transports de style HTTP, y compris la compression
d'en-tête HTTP à l'aide de QPACK - ce qui est similaire à la compression HTTP/2
appelée HPACK.

L'algorithme HPACK dépend d'une livraison *ordonnée* de flux, il n'a donc pas
été possible de le réutiliser pour HTTP/3 sans modifications depuis que QUIC
propose des flux pouvant être livrés dans le désordre. QPACK peut être considéré
comme la version de [HPACK](https://httpwg.org/specs/rfc7541.html) adaptée à QUIC.
