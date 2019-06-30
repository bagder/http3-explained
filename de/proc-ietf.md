## IETF

Die zur Standardisierung des Protokolls innerhalb der IETF eingerichteten QUIC-Arbeitsgruppe entschied bald, dass das QUIC-Protokoll auch andere Protokolle als "nur" HTTP übertragen können soll. Google-QUIC hatte lediglich HTTP transportiert - in der Praxis wurden HTTP/2 Frames mithilfe des HTTP/2 Frame Syntax transportiert.

Es wurde auch angegeben, dass IETF-QUIC seine Verschlüsselung und Sicherheit auf TLS 1.3 anstelle des für Google-QUIC eigens entwickelten Ansatzes stützen sollte.

Um die Anforderung zu erfüllen, mehr als nur HTTP zu transportieren, wurde die IETF-QUIC-Protokollarchitektur in zwei separate Schichten aufgeteilt: die Transport-QUIC-Schicht und die "HTTP-over-QUIC"-Schicht (letztere wird manchmal als "hq" bezeichnet).

Diese Teilung in Schichten - auch wenn sie harmlos klingt - hat dazu geführt, dass sich IETF-QUIC erheblich vom ursprünglichen Google-QUIC unterscheidet.

Die Arbeitsgruppe hat jedoch bald entschieden, dass sie sich auf die Bereitstellung von HTTP konzentriert, um eine rechtzeitige Auslieferung der ersten QUIC Version gewährleisten zu können. Damit wurde die Implementierung des Nicht-HTTP-Transports auf später verschoben.

Als wir im März 2018 mit der Arbeit an diesem Buch begonnen haben, war geplant, die endgültige Spezifikation für die erste QUIC Version im November 2018 auszuliefern. Dies wurde später auf Juli 2019 verschoben.

Während die Arbeit an IETF-QUIC vorangeschritten ist, hat das Google-Team Details aus der IETF-Version übernommen und langsam damit begonnen, ihre Version des Protokolls dahingehend weiterzuentwickeln, dass diese wie die IETF-Version aussieht. Google hat die eigene QUIC-Version weiterhin in ihrem Browser und ihren Diensten im Einsatz.

[Die meisten neuen Implementierungen, die sich aktuell in Entwicklung befinden,] (https://github.com/quicwg/base-drafts/wiki/Implementations) haben beschlossen, sich auf die IETF-Version zu konzentrieren und sind nicht mit der Google-Version kompatibel.