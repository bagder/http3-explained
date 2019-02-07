# Critiche comuni

## UDP non funzionerà mai

Una marea di aziende, operatori ed organizzazioni hanno l'abitudine di
bloccare o limitare tutto il traffico UDP non afferente alla porta 53 (DNS)
dato che [UDP] è stato spesso sfruttato in attacchi DDoS. Nello specifico
alcuni dei protocolli UDP esistenti e le rispettive implementazioni server,
sono stati recentemente coinvolti in attacchi detti "di amplificazione", dove
a partire da un piccolo volume di traffico si arriva a generare una vera e
propria onda di traffico, onde "mirate" verso un obiettivo innocente.

QUIC contiene una tecnica di mitigazione contro gli attacchi "amplificatori"
esigendo che il pacchetto iniziale consti almeno di 1200 bytes ed impiegando
una restrizione a livello di protocollo che IMPEDISCE al server di inviare una
risposta più grande di tre volte il volume della richiesta originale, senza
prima aver ricevuto un pacchetto di conferma dal client.

## UDP è lento nel kernel

Sembra essere vero, almeno ad oggi nel 2018. Non possiamo ovviamente predire
in che direzione andranno gli sviluppi, o quanto questo sia il risultato dei
lunghi anni di indifferenza da parte degli sviluppatori verso le prestazioni di
UDP stesso.

La maggior parte dei client non percepisce affatto questa lentezza.

## QUIC prende troppa CPU

Analogamente a quanto detto sopra -la critica "UDP è lento"- questa situazione
deriva dal fatto che TCP e TLS hanno goduto di molto più tempo per maturare,
per evolvere, ed hanno conseguentemente beneficiato di un supporto hardware e
software più cospicuo.

Abbiamo ragione di credere che questa situazione evolverà in futuro. Una
domanda rimane: fino a che punto questi problemi di CPU determineranno un
ostacolo per i responsabili della rete ?

## C'è solo Google

Non è vero. Google è reponsabile per aver presentato la prima specifica allo
IETF, dopo aver dimostrato la potenziale efficacia nell'adozione di un tale
protocollo, costruito sul gia noto UDP.

A partire da allora, una molteplicità di persone di compagnie ed entità
diverse ha lavorato all'interno dell'organizzazione neturale IETF, al fine di
creare un protocollo di trasporto standardizzato. Ovviamente, gli impiegati di
Google hanno participato al lavoro di gruppo, ma non dobbiamo trascurare un
gran numero di esperti che hanno interesse a contribuire all'evoluzione del
trasporto Internet, quali Mozilla, Fastly, Cloudflare, Akamai, Microsoft,
Facebook e Apple.

## Non rappresenta un gran miglioramento

Questa non è una vera critica ma piuttosto un'opinione. Magari è il caso,
magari il miglioramento non è davvero così netto considerando che HTTP/2 è
ancora molto recente.

Si suppone che HTTP/3 sarà più performante in reti con alto tasso di perdita
di pacchetti, oltre ad essere in grado di attuare una negoziazione più veloce;
la latenza percepita e la latenza effettiva ne beneficieranno sicuramente.
Saranno questi benefici sufficienti a motivare gli utenti e gli editori a
migrare verso un supporto per HTTP/3 a livello di servizi e software?
Solo il tempo ed un buon assessment delle prestazioni potranno rispondere!
