# API

Einer der Erfolgsfaktoren von regulärem TCP und Programmen, die dieses verwenden, ist die standardisierte Socket-API. Sie verfügt über gut definierte Funktionen und ermöglicht ein Verschieben von Programmen zwischen vielen verschiedenen Betriebssystemen, da TCP überall gleich funktioniert.

QUIC ist nicht so weit. Es gibt keine Standard-API für QUIC.

Bei QUIC muss eine der vorhandenen Implementierungen ausgewählt werden, bei deren API man bleiben muss. Dadurch werden Anwendungen bis zu einem gewissen Grad an eine einzelne Bibliothek "gebunden". Das Wechseln zu einer anderen Bibliothek bedeutet eine andere API und kann viel Arbeit erfordern.

Da QUIC normalerweise im User-space implementiert wird, kann es die Socket-API nicht einfach erweitern oder der vorhandenen TCP- und UDP-Funktionalität ähneln. Die Verwendung von QUIC bedeutet die Verwendung einer anderen API als der Socket-API.
