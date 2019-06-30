# Status

Die QUIC-Arbeitsgruppe hat seit Ende 2016 intensiv an der Festlegung der Protokolle gearbeitet. Es ist geplant, die Spezifikation bis Juli 2019 zu finalisieren.

Bis November 2018 gab es noch keine größeren Interoperabilitätstests mit HTTP/3 - nur mit den beiden vorhandenen Implementierungen, nicht aber mit einem Browser oder einer beliebten Open-Server Lösungen.

In den Wiki-Seiten der QUIC-Arbeitsgruppe werden rund fünfzehn verschiedene [QUIC Implementierungen aufgelistet](https://github.com/curl/curl/wiki/QUIC-implementation) - jedoch sind bei weitem nicht alle dieser Implementierungen mit den letzten Änderungen der Entwurfsspezifikation kompatibel. 

QUIC zu implementieren ist nicht einfach. Das Protokoll hat sich bis zu diesem Zeitpunkt ständig weiterentwickelt und verändert.

## Server

Es wurden keine öffentlichen Erklärungen hinsichtlich der Unterstützung von QUIC durch Apache oder Nginx abgegeben.

## Clients

Keiner der größeren Browser-Anbieter hat bisher eine Version ausgeliefert, mit der die IETF-Version von QUIC oder HTTP/3 ausgeführt werden kann.

Google Chrome wird seit vielen Jahren mit einer funktionsfähigen Implementierung von Googles eigener QUIC-Version ausgeliefert, die jedoch nicht mit dem IETF-QUIC-Protokoll kompatibel ist und deren HTTP-Implementierung sich von HTTP/3 unterscheidet.

## Implementierungshindernisse

QUIC hat sich dazu entschlossen, auf TLS 1.3 als Grundlage der Krypto- und Sicherheitsebene zu setzen, um sich auf ein zuverlässiges und bestehendes Protokoll stützen zu können. Jedoch hat sich die Arbeitsgruppe auch dazu entschieden, TLS in QUIC wirkungsvoller zu gestalten: es sollen lediglich "TLS messages" und nicht "TLS records" genutzt werden. 

Dies mag nach einer harmlosen Änderung klingen, hat jedoch für viele QUIC-Stack-Implementierer eine erhebliche Hürde bedeutet. Bestehende TLS-Bibliotheken, die TLS 1.3 unterstützen, verfügen einfach nicht über ausreichende APIs, um diese Funktionalität verfügbar zu machen und QUIC den Zugriff darauf zu ermöglichen. Während mehrere QUIC-Implementierer von größeren Organisationen stammen, die parallel an ihrem eigenen TLS-Stack arbeiten, gilt dies nicht für alle.

Das dominierende Open-Source-Schwergewicht OpenSSL zum Beispiel, hat keine API dafür - und hat bisher auch keinen Wunsch geäußert, eine solche bald zur Verfügung zu stellen (Stand November 2018).

Dies wird letztendlich auch zu Hindernissen bei der Bereitstellung führen, da sich QUIC-Stacks entweder auf andere TLS-Bibliotheken stützen müssen, einen separat gepatchten OpenSSL-Build verwenden müssen oder ein Update auf eine zukünftige OpenSSL-Version benötigen.

## Kernel und CPU-Last

Sowohl Google als auch Facebook haben angemerkt, dass die Bereitstellung von QUIC in großem Umfang ungefähr die doppelte Menge an CPU-Rechenleistung erfordert als wenn die gleiche Traffic-Last via HTTP/2 über TLS abgewickelt würde.

Einige Erklärungen hierfür sind:

- Teile von UDP sind vor allem unter Linux nicht so optimiert wie der TCP-Stack, da UDP traditionell nicht für solche Hochgeschwindigkeitsübertragungen verwendet wurde.

- TCP- und TLS-Offloading auf Hardware ist vorhanden, bei UDP jedoch viel seltener und bei QUIC im Grunde nicht vorhanden.

Daher gibt es Gründe zur Annahme, dass sich die Leistung und die CPU-Anforderungen im Laufe der Zeit verbessern werden.