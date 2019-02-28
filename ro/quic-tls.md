# Conexiunile folosesc TLS

Imediat după primul pachet care stabilește o conexiune, inițiatorul trimite un 
frame criptografic care începe stabilirea handshake-ului pentru layer-ul de 
securitate.

Nu există nicio cale de a evita acest lucru sau de a evita folosirea TLS pentru 
conexiune QUIC. Protocolul este proiectat pentru a îngreuna manipulările 
middlebox-urilor, cu scopul de a evita osificarea protocolului.
