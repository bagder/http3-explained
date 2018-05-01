## Ossification

Anche le modifiche al TCP soffrono dei problemi conseguenti alle middle-boxes
dato che alcune delle nuove opzioni TCP sono interpretate e bloccate dato che
sconosciute ai più. Questo condizione è detta "ossificazione del protocollo".
Se viene loro permesso di ispezionare i dettagli di protocollo, il sistema
impara a riconoscere il comportamento tipico di un protocollo e nel tempo 
diventerà difficile se non appunto impossibile modificare tali assunzioni.

La sola vera ed efficace strategia per il contrasto della "ossificazione" è
utilizzare in maniera estensiva la cifratura, cosi da impedire ai box
intermedi di desumere (distinguere) quale protocollo stia passando sotto il
loro ponte.
