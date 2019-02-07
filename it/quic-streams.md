# Streams (flussi)

I flussi QUIC permettono l'astrazione leggera e ordinata della sequenza di bytes.

Esistono due tipi di flussi (streams) in QUIC:

 - Flussi unidirezionali che trasportano dati in una sola direzione: dal produttore dello stream all'altro estremo, il destinario.

 - Flussi bidirezionali che permettono di inviare dati in entrambe le direzioni.

Ciascuno dei due tipi di flusso può essere creato da ognuno dei due estremi,
può inviare dati allo stesso tempo su flussi alternati, o può essere soppresso.

Per mandare dati all'interno di una connession QUIC, è necessario utilizzare
uno o più flussi.

## Controllo di flusso

I flussi sono controllati individualmente, peremettendo ad ogni estremo di
limitare l'allocazione della memoria e di applicare una pressione inversa.
La creazione dei flussi è anch'essa soggetta a controllo di flusso; si
richiede ad ogni peer di dichiarare l'ID di flusso "massimo" al quale si è
disposti ad arrivare (dunque l'ID corrisponde al numero totale di flussi
gestibili da ogni estremo).

## Identificatori di flusso

I flussi sono definiti da un intero di 62-bit privo di segno, al quale si è
soliti riferirsi come "Stream ID". All'interno dello Stream-ID, i due bits
meno significativi sono utilizzati per identificare il tipo di flusso (uni o
bi-direzionale) e chi abbia inizializzato la comunicazione.

Il bit meno significativo dello Stream-ID (0x1) identifica chi dei due abbia
inizializzato il flusso. In caso sia il client ad iniziare la connessione il
numero di flusso risulterà parii (LSB a 0); tale numero sarà dispari in caso
di flusso iniziato dal server (LSB a 1).

Il secondo bit meno significativo dello Stream-ID (0x2) è utilizzato per
distinguere fra flussi uni e bi-direzionali. Flussi unidirezionali avranno
impostato il bit a 1, flussi bidirezionali utilizzeranno sempre il valore 0.

## Concorrenza di flussi

QUIC permette ad un numero arbitrario di flussi di operare in concomitanza.
Un estremo limita il numero di flussi concorrenti in entrata comunicando lo
Stream-ID massimo che è disposto ad accettare.

Il massimo valore di Stream-ID è specifico ad ogni estremo e si applica solo
all'estremità che riceve tale impostazione.

## Spedire e ricevere dati

Gli end-points utilizzano i flussi per spedire e ricevere dati. In fondo è
questo il loro fine ultimo. Gli streams sono un flusso "astratto" di bytes
ordinati. Streams separati non saranno necessariamente consegnati nello
stesso ordine di invio.

## Prioritizzazione dei flussi

Il multiplexing dei flussi ha un impatto significativo sulle performance
dell'applicazione, in caso le risorse assegnatevi siano correttamente
ordinate per priorità. L'esperienza con altri protocolli multiplexati -quale
HTTP/2- mostra che una buona strategia di prioritizzazione ha certamente un
impatto positivo sulle prestazioni.

QUIC in se non mette a disposizione frames adatti a scambiare informazioni
sullo stato delle priorità. Al contrario si accontenta di ricevere tali
informazioni direttamente dall'applicazione essa stessa basata su QUIC.
I protocolli che utilizzano QUIC sono liberi di definire il proprio schema di
prioritizzazione secondo le proprie necessità e semantiche applicative. 

Quando si utilizza HTTP/3 su QUIC, la prioritizzazione è gestita all'interno
dello strato HTTP.
