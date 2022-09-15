# API

Uno de los factores de éxito de TCP regular y de los programas que lo utilizan,
es la API de sockets estandarizada. Tiene una funcionalidad bien definida y 
usando esta API puedes mover programas entre muchos sistemas operativos 
diferentes ya que TCP funciona el mismo.

QUIC no está ahí. No hay una API estándar para QUIC.

Con QUIC, tienes que elegir una de las implementaciones de bibliotecas
existentes y y seguir su API. Esto hace que las aplicaciones estén "encerradas"
en una sola biblioteca hasta una sola biblioteca. Cambiar a otra biblioteca 
significa otra API y eso podría implicar mucho trabajo.

Además, como QUIC se implementa normalmente en el espacio de usuario, no puede
fácilmente extender la API del socket o aparecer de forma similar a la 
funcionalidad existente de TCP y UDP. existentes. Usar QUIC significará usar 
otra API además de la API de sockets.
