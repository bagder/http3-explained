## Mai multe fluxuri în conexiuni

Similar cu SCTP, SSH și HTTP/2, QUIC oferă fluxuri logice separate în interiorul 
conexiunilor fizice - in număr de fluxuri paralele care pot transfera informații 
simultan peste o singură conexiune fără să afecteze celelalte fluxuri.

O conexiune este negociere între două sisteme, similar cu modul de funcționare 
al TCP. O conexiune QUIC este făcută pe un port UDP și o adresă de IP, dar, 
odată stabilită, conexiunea este asociată cu propriul "ID de conexiune".

Peste o conexiune stabilită, oricare dintre părți poate crea fluxuri și să 
trimită informații la celălalt capăt. Fluxurile sunt livrate în ordinea în care 
sunt trimise și sunt fiabile, dar este posibil ca fluxuri diferite să fie 
livrate într-o altă ordine.

QUIC oferă control și asupra conexiunilor și a fluxurilor.

Puteți citi mai multe detalii în secțiunile [conexiuni](quic-connections.md) și 
[fluxuri](quic-streams.md).
