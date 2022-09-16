# QUIC v2

Con el fin de conseguir el mayor enfoque posible en el núcleo del protocolo QUIC
y ser capaz de enviarlo a tiempo, varias características que fueron
originalmente planificadas para ser parte del núcleo del protocolo se han
pospuesto y ahora están previstas para ser realizadas en una versión posterior
de QUIC. QUIC versión 2 o posterior.

Sin embargo, el autor de este documento tiene una bola de cristal bastante
defectuosa, por lo que no podemos decir con seguridad qué características
aparecerán o no en la versión 2. Sin embargo, podemos mencionar algunas de las
características y cosas que explícitamente han sido eliminadas del trabajo de
la v1 para ser "trabajadas más tarde" y que entonces posiblemente podrían
aparecer en una versión 2.

## Corrección de errores hacia delante

La corrección de errores hacia adelante (FEC) es un método para obtener el
control de errores en la transmisión de datos en el que el transmisor envía
datos redundantes y el receptor reconoce sólo la parte de los datos que no
contiene errores aparentes.

Google experimentó con esto en su trabajo original de QUIC, pero posteriormente
se eliminó de nuevo ya que los experimentos no salieron bien. Esta
característica es objeto de discusión para QUIC v2 pero probablemente se
necesita que alguien demuestre que realmente puede ser una adición útil sin
demasiada penalización.

## Multipath

Multipath significa que el transporte puede por sí mismo utilizar múltiples
rutas de red para maximizar el uso de recursos y aumentar la redundancia.

A los defensores de SCTP del mundo les gusta mencionar que SCTP ya cuenta con
multipath y también lo hace el TCP moderno.

## Datos no fiables

Se ha discutido la posibilidad de ofrecer flujos "no fiables" como opción, lo
que permitiría a QUIC sustituir también a las aplicaciones de tipo UDP.

## Adaptaciones no-HTTP

DNS sobre QUIC fue uno de los primeros protocolos no-HTTP mencionados que podría
recibir algo de atención una vez que QUIC v1 y HTTP/3 sean lanzados. Pero con
un nuevo transporte como este que se ha traído al mundo no puedo imaginar que
se detenga ahí.
