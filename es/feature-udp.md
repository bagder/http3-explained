## Protocolo de transferencia sobre UDP

QUIC es un protocolo de transferencia implementado sobre UDP. Si observas 
casualmente el tráfico de tu red, verás que QUIC aparece como paquetes UDP.

Basado en UDP también utiliza números de puerto UDP para identificar servicios
de red específicos en una dirección IP determinada.

Todas las implementaciones conocidas de QUIC están actualmente en el espacio de
usuario, lo que permite una evolución más rápida de lo que suelen permitir las
implementaciones en el espacio del núcleo.

## ¿Funcionará?

Hay empresas y otras configuraciones de red que bloquean el tráfico UDP en otros
puertos que no sean el 53 (utilizado para el DNS). Otros estrangulan tales datos
de manera que hace que QUIC funcione peor que los protocolos basados en TCP. No
hay fin a lo que algunos operadores pueden hacer.

En un futuro previsible, todo uso de transportes basados en QUIC probablemente 
tendrá que ser capaz de retroceder con gracia a otra alternativa (basada en 
TCP). Los ingenieros de Google han mencionado anteriormente tasas de fallo 
medidas en porcentajes de un solo dígito.

## ¿Mejorará?

Lo más probable es que si QUIC demuestra ser una valiosa adición al mundo de
Internet, la gente querrá utilizarlo y querrá que funcione en sus redes y 
entonces las empresas podrían empezar a reconsiderar sus obstáculos. Durante los
años en que ha progresado el desarrollo de QUIC, el índice de éxito para 
establecer y utilizar conexiones QUIC en Internet ha aumentado.
