# Spin Bit (Bit rotante)

Una delle discussioni più estenuanti all'interno del gruppo di lavoro QUIC
. oggetto di mille emails e ore di dispute verbali- è legata ad un singolo
bit: il bit rotante (spin bit).

I fautori dello spin-bit insistono nell'affermare quanto -per operatori ed
amministratori di rete- sia fondamentale poter misurare la latenza fra due
end-points QUIC.

Gli opppositori dello spin-bit temono una potenziale fuga di informazioni.

## Girare un bit

Entrambi gli estremi mantengono temporaneamente un valore di 0 o 1 per ogni
singola connessione QUIC; client e server sono incaricati di impostare un
valore all'interno di ciascun pacchetto spedito.

Entrambi gli estremi inviano il pacchetto impostando lo stesso valore per
la durata di un solo round-trip, e dopo invertono il valore. Il risultato è
dunque una serie di pulsazioni di 0 e 1 utile al monitoraggio.

Questo tipo di misurazione è efficace solo se il peer che invia non è
limitato a livello di applicazione o di controllo di flusso, in assenza di
riordino di pacchetti (causato dalla rete stessa).
