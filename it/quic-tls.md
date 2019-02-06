# Connessioni su TLS

Successivamente al pacchetto iniziale che si occupa di istanziare la
connessione, l'estremo che ha iniziato la connessione invierà un
"crypto-frame" che scaturisce la negoziazione dello strato di sicurezza.
Lo strato di sicurezza si basa su TLS 1.3.

Non vi è modo di evitare o declinare l'uso di TLS per una connessione QUIC.
Il protocollo è specificamente concepito per evitare che le "middle-boxes"
possano intercettare o modificare il traffico, allo scopo di evitare una
ossificazione prematura del protocollo.
