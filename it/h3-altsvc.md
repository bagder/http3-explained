# Alt-svc

L'intestazione di servizio alternativo (Alt-svc:) e il corrispettivo frame
HTTP/2 `ALT-SVC` non sono specificamente creati per QUIC o HTTP/3.
Tali header sono parte di un meccanismo gia ben rodato per cui un server può
segnalare ad un client *"guarda, io erogo questo stesso servizio ANCHE su 
QUESTO HOST, utilizzando QUESTO PROTOCOLLO, su QUESTA PORTA"*. Vedi i dettagli
nella [RFC 7838](https://tools.ietf.org/html/rfc7838).

In caso lo supportasse e lo desiderasse, ad un client che ricevesse tale header
Alt-Svc in una risposta verrebbe consigliato di connettersi in parallelo ed in
background all'host suggerito -utilizzando il protocollo definito- ed in
seguito completare il resto delle operazioni utilizzando questo nuovo canale,
al posto della connessione iniziale. 

In caso la connessione iniziale stesse utilizzando HTTP/2 o addirittura HTTP/1,
il server può decidere di rispondere al client di riprovare tale connessione
via HTTP/3. Tale connessione potrebbe essere diretta allo stesso host, o ad un
altro host distante, capace di servire tale contenuto sul protocollo prescelto.
L'informazione fornita all'interno dell'header Alt-Svc è dotata di una data di
scadenza, che permette la redirezione dei clients verso host alternativi entro
un certo lasso temporale.

## Esempio

Un server HTTP include nella propria risposta un header di tipo `Alt-Svc:`:

    Alt-Svc: h3=":50781"

Questo indica che HTTP/3 è disponibile via UDP sulla porta 50781, sullo stesso
host utilizzato in prima istanza.

Un client può a quel punto tentare di stabilire una connessione QUIC verso la
destinazione indicata, ed in caso di successo continuerebbe a comunicare con
l'origine attraverso il nuovo canale, non attraverso l'originale in HTTP.
