# Ossifikation

Das Internet ist ein Netzwerk der Netzwerke. Um sicherzustellen, dass dieses Netzwerk der Netzwerke so funktioniert, wie es soll, gibt es Infrastruktur an vielen verschiedenen Plätzen. Diese Geräte - jene Boxen, die über das Netzwerk verteilt sind - bezeichnen wir manchmal als "Middle-Boxes". Boxen, die irgendwo zwischen den beiden Endpunkten sitzen und die primären Beteiligten in einem traditionellen Netzwerk-Datentransfer sind.

Diese Boxen dienen vielen verschiedenen spezifischen Zwecken - aber ich glaube sagen zu können, dass sie dort genutzt werden, weil jemand glaubt, dass diese dort sein müssen, damit alles funktioniert.

Middle-Boxes leiten IP-Pakete zwischen Netzwerken, sie blockieren böswilligen Traffic, führen die NAT (Network Address Translation, zu Deutsch "Netzwerkadressübersetzung") durch, verbessern die Leistung, manche versuchen den Traffic auszuspionieren und vieles mehr.

Um ihren Pflichten gerecht zu werden, müssen diese Boxen Networking und jene Protokolle kennen, die sie überwachen oder modifizieren. Dazu nutzen sie Software - die aber nicht oft aufgerüstet wird.

Auch wenn sie wie Klebstoff das Internet zusammenhalten, halten sie oft nicht mit der neuesten Technologie mit. Die Mitte eines Netzwerks verändert sich nicht so schnell wie die Enden, wie die Clients und Server dieser Welt. 

Die Netzwerkprotokolle, die diese Boxen inspizieren wollen und kennen, haben dann folgendes Problem: die Boxen wurden vor einiger Zeit ausgeliefert, als die Protokolle gewisse Features hatten. Neue Features oder Veränderungen in der Verhaltensweise riskieren, dass Boxen diese als schlecht oder illegal interpretieren. Solcher Traffic könnte fallen gelassen oder verzögert werden - bis hin zu einem Ausmaß, dass User diese Features nicht nutzen wollen.

Das wird "Protokoll-Ossifikation" genannt.

Änderung an TCP leiden auch an Ossifikation: einige Boxen zwischen einem Client und einem entfernten Server erkennen neue TCP Optionen und blockieren solche Verbindungen, weil diese die Optionen nicht kennen. Wenn sie Protokolldetails erkennen dürfen, werden Systeme lernen, wie sich Protokolle normalerweise verhalten und im Laufe der Zeit wird es unmöglich sie zu ändern.

Der einzig effektive Weg um Ossifikation zu bekämpfen, ist die Verschlüsselung von so viel Kommunikation wie möglich. Damit werden Middle-Boxes daran gehindert, von durchgeleiteten Protokollen viel einsehen zu können.
