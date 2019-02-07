# 0-RTT

Per ridurre il tempo richiesto per stabilire una nuova connessione, un client che si sia
precedentemente collegato ad un server potrebbe mantenere in cache alcuni parametri relativi
a tale connessione ed utilizzarli successivamente per iniziare una connessione a **0-RTT**
con il server. Questa modalità permette al client di inviare dati fin dal primo pacchetto,
senza dover aspettare il termine della negoziazione stessa.
