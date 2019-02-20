## Nivelurile de aplicație și de transfer

Protocolul IETF QUIC este un protocol de transfer, peste care pot fi folosite 
alte protocoale. Layer-ul inițial de aplicație al protocolului este HTTP/3 (h3).

Layer-ul de transfer susține și conexiuni și fluxuri.

Versiunea inițială de QUIC a Google lipea transferul și HTTP împreună într-un 
singur protocol "bun la toate" și reprezenta un protocol specializat de 
trimitere-frame-uri-http/3-peste-udp.
