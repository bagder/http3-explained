# Flujos

Los flujos en QUIC proporcionan una abstracción ligera y ordenada de flujos de 
bytes.

Hay dos tipos básicos de flujos en QUIC:

 - Los flujos unidireccionales transportan datos en una dirección: desde el 
   iniciador del flujo a su par.

 - Los flujos bidireccionales permiten el envío de datos en ambas direcciones.

Cualquier tipo de flujo puede ser creado por cualquier end-point, puede enviar
datos simultáneamente intercalados con otros flujos, y puede ser cancelado.

Para enviar datos a través de una conexión QUIC, se utilizan uno o más flujos.

## Control de flujo

Los flujos se controlan individualmente, lo que permite a un end-point limitar 
el compromiso de memoria y aplicar presión de retorno. La creación de flujos 
también está controlada por el flujo, con cada par declarando el máximo ID de
flujo que está dispuesto a aceptar en un momento dado.

## Identificadores de flujos

Los flujos se identifican mediante un número entero sin signo de 62 bits,
denominado ID del flujo. Los dos bits menos significativos del ID de flujo se
utilizan para identificar el tipo de flujo (unidireccional o bidireccional) y el
iniciador del flujo.

El bit menos significativo (0x1) del ID de flujo identifica al iniciador del 
flujo. Los clientes inician los flujos pares (los que tienen el bit menos 
significativo en 0); los servidores inician los flujos impares (con el bit en 
1).

El segundo bit menos significativo (0x2) del ID del flujo diferencia entre los
flujos unidireccionales y los bidireccionales. Los flujos unidireccionales 
siempre tienen este bit a 1 y los bidireccionales a 0.

## Concurrencia de flujos

QUIC permite que un número arbitrario de flujos operen simultáneamente. Un 
end-point limita el número de flujos entrantes concurrentemente activos 
limitando el ID máximo del flujo.

El ID de flujo máximo es específico para cada end-point y se aplica sólo al 
peer que recibe la configuración.

## Envío y recepción de datos

Los end-points utilizan flujos para enviar y recibir datos. Ese es, después de
todo, su propósito final. Los flujos son una abstracción ordenada de flujos de
bytes. Sin embargo, los flujos separados no se entregan necesariamente en el
orden original.

## Priorización de flujos

La multiplexación de flujos tiene un efecto significativo en el rendimiento de 
la aplicación si los recursos asignados a los flujos se priorizan correctamente.
La experiencia con otros protocolos multiplexados, como HTTP/2, muestra que las
estrategias de priorización eficaces tienen un impacto positivo significativo en
el rendimiento.

El propio QUIC no proporciona tramas para intercambiar información de
priorización. En su lugar, depende de la recepción de información de prioridad
de la aplicación que utiliza QUIC. Los protocolos que utilizan QUIC pueden
definir cualquier esquema de priorización que se adapte a la semántica de su 
aplicación.

Se ha criticado el modelo de priorización de HTTP/2, y se teme que sea demasiado
complejo y que no sea utilizado ni implementado por muchos servidores HTTP/2.
Por ahora, la priorización en HTTP/3 se ha eliminado de la especificación 
principal de HTTP/3 y se está trabajando en ella como una [especificación 
separada] (https://tools.ietf.org/html/draft-ietf-httpbis-priority).
