## Secure

QUIC è sempre sicuro. Non esiste alcuna versione clear-text del protocollo,
così che l'aver negoziato QUIC implica l'impiego di crittografia e sicurezza
TLS 1.3. Come detto in precedenza, tale pratica impedisce l'ossificazione
ed ogni altra sorta di blocco o trattamento speciale, olre ad assicurarsi che
QUIC abbia tutte le proprietà di sicurezza HTTPS che gli utilizzatori web si
attendono e desiderano.

Solo una piccola parte dei primi pacchetti della negoziazione iniziale sono
trasmessi in chiaro, prima che il protocollo di cifratura venga negoziato.
