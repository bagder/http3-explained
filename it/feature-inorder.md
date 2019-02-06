## Consegna ordinata

QUIC garantisce una consegna ordinata dei flussi, ma non fra i flussi stessi.
Questo significa che ogni flusso invierà dati e manterrà un ordine fra tali
dati, ma ogni singolo flusso potrebbe raggiungere la destinazione in un ordine
diverso da quello in cui l'applicazione lo avesse inizialmente spedito!

Per esempio: lo stream A e B sono trasferiti dal server al client. Il flusso A
inizia per primom il B segue. In QUIC, la perdita di un pacchetto influenza
solamente lo stream al quale tale pacchetto perso appartiene. Se uno stream A
perdesse un pacchetto ma lo stream B no, il flusso B continuerebbe il proprio
trasferimento mentre il pacchetto perso dallo stream A verrebbe ritrasmesso.
Ciò non era possibile in HTTP/2.

Qui di seguito illustrati in giallo e blu due flussi inviati attraverso QUIC
all'interno di una singola connessione. Essi sono indipendenti e potrebbero
arrivare in un ordine diverso da quello inizialmente previsto, pur venendo
entrambi consegnati correttamente a livello di applicazione, in ordine.

![due flussi QUIC tra due computer](../images/quic-chain-streams.png)
