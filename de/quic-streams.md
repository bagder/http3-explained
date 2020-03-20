# Streams

QUIC Streams bieten eine einfache, geordnete Byte-Stream-Abstraktion.

In QUIC gibt es zwei grundlegende Arten von Streams:

 - Unidirektionale Streams übertragen Daten in eine Richtung: vom Initiator des Streams zu seinem Peer.

 - Bidirektionale Streams ermöglichen das Senden von Daten in beide Richtungen.

Jeder Stream-Typ kann von jedem Endpunkt erstellt werden, gleichzeitig mit anderen Streams verschachtelte Daten senden und abgebrochen werden.

Um Daten über eine QUIC-Verbindung zu senden, werden ein oder mehrere Streams verwendet.

## Ablaufsteuerung

Streams werden individuell ablaufgesteuert, sodass ein Endpunkt die Speicherbindung begrenzen und Gegendruck ausüben kann. Die Erstellung von Streams wird ebenfalls ablaufgesteuert, wobei jeder Peer die maximale Stream-ID angibt, die er zu einem bestimmten Zeitpunkt akzeptieren möchte.

## Stream Identifikatoren

Streams werden durch eine vorzeichenlose 62-Bit-Ganzzahl identifiziert, die als Stream-ID bezeichnet wird. Die niedrigstwertigen zwei Bits der Stream-ID werden verwendet, um den Stream-Typ (unidirektional oder bidirektional) und den Initiator des Streams zu identifizieren.

Das niedrigstwertige Bit (0x1) der Stream-ID identifiziert den Initiator des Streams. Clients initiieren geradzahlige Streams (solche mit dem niedrigstwertigen Bit auf 0); Server initiieren ungeradzahlige Streams (wobei das Bit auf 1 gesetzt ist).

Das zweitniedrigste Bit (0x2) der Stream-ID unterscheidet zwischen unidirektionalen und bidirektionalen Streams. Bei unidirektionalen Streams ist dieses Bit immer auf 1 gesetzt, und bei bidirektionalen Streams ist dieses Bit auf 0 gesetzt.

## Gleichzeitigkeit von Streams

Mit QUIC kann eine beliebige Anzahl von Streams gleichzeitig betrieben werden. Ein Endpunkt begrenzt die Anzahl der gleichzeitig aktiven eingehenden Streams, indem die maximale Stream-ID begrenzt wird.

Die maximale Stream-ID ist für jeden Endpunkt spezifisch und gilt nur für den Peer, der die Einstellung erhält.

## Daten senden und empfangen

Endpunkte verwenden Streams zum Senden und Empfangen von Daten - das ist immerhin ihr letztendlicher Zweck. Streams sind eine geordnete Byte-Stream-Abstraktion. Separate Streams werden jedoch nicht unbedingt in der ursprünglichen Reihung ausgeliefert.

## Stream Priorisierung

Stream-Multiplexing hat erhebliche Auswirkungen auf die Anwendungsleistung, wenn den Streams zugewiesene Ressourcen korrekt priorisiert werden. Die Erfahrung mit anderen Multiplex-Protokollen - wie HTTP/2 - zeigt, dass effektive Priorisierungsstrategien einen signifikanten positiven Einfluss auf die Leistung haben.

QUIC selbst bietet keine Frames für den Austausch von Priorisierungsinformationen. Stattdessen müssen Prioritätsinformationen von der Anwendung empfangen werden, die QUIC verwendet. Protokolle, die QUIC verwenden, können jedes Priorisierungsschema definieren, das ihrer Anwendungssemantik entspricht.

Wenn HTTP/3 über QUIC verwendet wird, erfolgt die Priorisierung in der HTTP-Schicht.
