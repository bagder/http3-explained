## TLS 1.3

La sicurezza del trasporto utilizzato da QUIC si basa su TLS 1.3 ([RFC
8446](https://tools.ietf.org/html/rfc8446)) quindi non esistono connessioni
QUIC non criptate.

TLS 1.3 presenta molteplici vantaggi se paragonato alle versioni precedenti;
una delle principali ragioni dell'adozione di TLS da parte di QUIC consiste
nel fatto che la 1.3 ha modificato la modalità di negoziazione al fine di
richiedere meno va-e-vieni (round-trips). Ciò riduce la latenza del protocollo.

La versione oramai "legacy" di Google-QUIC utilizzava un algoritmo di
cifratura personalizzato, non-standard.
