# Priorización de HTTP/3

Como se ha mencionado anteriormente, la priorización entre flujos se ha
eliminado de la especificación principal de HTTP/3 para trabajar en ella por
separado.

Esto se debe a lo aprendido del modelo de priorización de HTTP/2 y su
implementación (o falta de ella) en el mundo real.

Se ha propuesto un [modelo de priorización más sencillo que el de HTTP/2]
(https://tools.ietf.org/html/draft-ietf-httpbis-priority) que utiliza campos de
cabecera HTTP con un número limitado de ajustes de prioridad. Se trata de un
cambio clave con respecto a los indicadores de dependencia y peso en los marcos
de cabecera de HTTP/2 y permite una mejor comprensión en la capa de
aplicación.

La repriorización, y la posibilidad de apoyarla, todavía se está debatiendo.
HTTP/2 tenía marcos de priorización para manejar esto, pero los verdaderos
flujos independientes en QUIC y HTTP/3 hacen que esto sea más complicado, por
lo que todavía se están debatiendo los beneficios frente a la complejidad.

Cuando se acuerde (¡o si se acuerda!) un mejor modelo de priorización para 
HTTP/3, se espera poder trasladarlo también a HTTP/2, para resolver la 
complejidad y los problemas de implementación.
