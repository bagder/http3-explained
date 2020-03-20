# Spin Bit

Eine der vielleicht längsten Designdiskussionen innerhalb der QUIC-Arbeitsgruppe - Gegenstand von mehreren hundert Mails und stundenlangen Diskussionen - betrifft ein einziges Bit: das Spin Bit.

Die Befürworter dieses Bits bestehen darauf, dass Operatoren und Personen zwischen zwei QUIC-Endpunkten die Latenz messen können.

Die Gegner dieser Funktion mögen das potenzielle Informationsleck nicht.

## Ein Bit drehen

Beide Endpunkte, der Client und der Server, behalten für jede QUIC-Verbindung den Spin-Wert 0 oder 1 bei und setzen das Spin Bit für Pakete, die für diese Verbindung gesendet werden, auf den entsprechenden Wert.

Beide Seiten senden dann Pakete aus, bei denen das Spin Bit auf den gleichen Wert gesetzt ist solange ein Roundtrip dauert, und schalten dann den Wert um. Der Effekt ist dann ein Impuls von Einsen und Nullen in dem Bitfeld, das Beobachter überwachen können.

Diese Messung funktioniert nur, wenn der Absender weder auf die Anwendung noch auf die Flusskontrolle beschränkt ist. Die Neuordnung von Paketen über das Netzwerk kann  auch zu unscharfen Daten führen.