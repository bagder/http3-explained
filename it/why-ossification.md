# Ossificazione

Internet è una rete fatta di reti. In diversi punti del mondo -sulla rotta fra
le varie reti interconnesse- sono installati dispositivi che assicurano il
buon instradamento e funzionamento della rete. Questi dispositivi -i varii
componenti distribuiti della rete- sono comunemente chiamati "middle-boxes".
Scatole che semplicemente si trovano in mezzo al percorso fra i due end-points
e che a loro volta sono coinvolte nel trasferimento dati via rete.

Questi apparecchi servono molteplici funzioni ma limitiamoci semplicemente a
concludere che se qualcuno li ha installati in tali specifici punti della rete,
avrà sicuramente avuto i suoi buoni motivi. 

Tali "middle-boxes" instradano i pacchetti IP fra le differenti reti globali,
bloccano il traffico maligno, si occupano di tradurre gli indirizzi di rete
(NAT - Network Address Translation), aumentano le prestazioni, tentano in
certi casi di spiare il traffico passante, ed altro ancora.

Al fine di espletare i propri compiti, questi dispositivi devono avere
conoscenza di "networking" e dei protocolli oggetto del traffico stesso.
Appositi software sono sviluppati allo scopo, software che tuttavia non
ricevono aggiornamenti troppo frequenti.

A parte essere ovviamente i "collanti" che tengono insieme Internet, questi
dispositivi al cuore della rete non sono mai altrettanto avanzati in termini
di tecnologia quanto quelli agli estremi della rete, ossia clients e servers.

Tutti protocolli di rete che queste macchine potrebbero voler ispezionare e
di cui potrebbero voler decidere la sorte in base a origine o contenuto,
subiscono questo problema: tali macchine sono state installate in conformità
con le opzioni di protocollo disponibili all'epoca e non sono flessibili.
Aggiunte o modifiche del comportamento non note in precedenza potrebbero fare
si che il dispositivo interpreti in maniera non corretta il pacchetto,
scartandolo per malformazione o contenuto ritenuto erroneamente illecito.
Tale traffico subirebbe rallentamenti o drop improvvisi al punto da rendere
tali nuove opzioni di protocollo indesiderabili da un punto di vista utente.

Siamo di fronte a ciò che possiamo definire "ossificazione del protocollo".

Anche le modifiche al TCP soffrono di ossificazione: alcune delle nuove
opzioni TCP sono interpretate e bloccate in quanto sconosciute ai più.
Se viene permesso al dispositivo di ispezionare in dettaglio il protocollo,
il sistema tederà a definire pattern standard di comportamento per un
determinato protocollo e nel tempo diventerà difficile se non appunto
impossibile modificare tali assunzioni.

La sola vera ed efficace strategia per il contrasto della "ossificazione" è
utilizzare in maniera estensiva la cifratura, cosi da impedire ai box intermedi
di desumere (distinguere) quale protocollo stia passando sotto il loro ponte.
