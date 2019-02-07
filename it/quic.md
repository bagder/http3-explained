# How QUIC works

Senza voler dettagliare esattamente bits e bytes °on the wire°, questa sezione si
occupa di descrivere i blocchi fondamentali al funzionamento del protocollo di
trasporto QUIC. Se vuoi implementare QUIC nel tuo proprio stack, questa descrizione
dovrebbe esserti d'aiuto a comprenderne le basi; per maggiori dettagli meglio fare
riferimento alle bozze ufficiali e alle RFC pubblicate da IETF.

1. Inizializzare una [connessione](quic-connections.md)
2. ... che includa [sicurezza TLS](quic-tls.md)
3. Infine usare i [flussi](quic-streams.md)
