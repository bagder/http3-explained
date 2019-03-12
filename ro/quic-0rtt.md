# 0-RTT

Pentru a reduce timpul necesar stabilirii unei noi conexiuni, o 
aplicație-client, care s-a conectat în trecut la un server, are posibilitatea să 
salveze în cache anumiți parametri și, ulterior, să stabilească o conexiune 
**0-RTT** cu server-ul. Asta permite aplicației-client să trimită informații 
imediat, fără să aștepte ca handshake-ul să fie finalizat.
