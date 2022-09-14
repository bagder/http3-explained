# Estado

El grupo de trabajo de QUIC ha trabajado intensamente desde finales de 2016 en
la especificación de los protocolos y se está acercando a las etapas finales en
el momento de escribir este artículo (junio de 2020).

Durante 2019 y 2020 ha habido un número creciente de [pruebas de 
interoperabilidad con HTTP/3](https://docs.google.com/spreadsheets/d/1D0tW89vOoaScs3IY9RGC0UesWGAwE6xyLk0l4JtvTVg)
y las CDN y los navegadores han comenzado a lanzar el soporte inicial - aunque a
menudo detrás de flags.

Hay un número de diferentes [implementaciones de QUIC 
listadas](https://github.com/quicwg/base-drafts/wiki/Implementations) en las
páginas wiki de los grupos de trabajo de QUIC.

Implementar QUIC no es fácil y el protocolo ha seguido moviéndose y cambiando
incluso hasta la fecha.

## Servidores

El soporte de NGINX para QUIC y HTTP/3 está en desarrollo y se ha anunciado una
[versión preliminar](https://www.nginx.com/blog/introducing-technology-preview-nginx-support-for-quic-http-3/).

No ha habido ninguna declaración pública en términos de soporte para QUIC por 
parte de Apache.

## Clientes

Ninguno de los grandes proveedores de navegadores ha lanzado aún ninguna 
versión, en ningún estado, que pueda ejecutar la versión IETF de QUIC o HTTP/3.

Google Chrome ha sido distribuido con una implementación funcional de la propia
versión de QUIC de Google desde hace muchos años y recientemente ha comenzado a
soportar la versión del IETF detrás de un flag. Firefox también lo soporta 
con una flag.

curl envió el primer soporte experimental de HTTP/3 (draft-22) en la versión
7.66.0 el 11 de septiembre de 2019. curl utiliza la biblioteca Quiche de 
Cloudflare o la familia de bibliotecas ngtcp2 para realizar el trabajo.

## Obstáculos de implementación

QUIC decidió utilizar TLS 1.3 como base para la capa de criptografía y seguridad
para evitar inventar algo nuevo y en su lugar apoyarse en un protocolo existente
y de confianza. Sin embargo, al hacer esto, el grupo de trabajo también decidió
que para realmente racionalizar el uso de TLS en QUIC, sólo debería utilizar
"mensajes TLS" y no "registros TLS" para el protocolo.

Esto puede parecer un cambio inocuo, pero en realidad ha causado un obstáculo 
importante para muchos implementadores de la pila QUIC. Las librerías TLS 
existentes que soportan TLS 1.3 simplemente no tienen APIs suficientes para
exponer esta funcionalidad y permitir a QUIC acceder a ella. Aunque varios 
implementadores de QUIC provienen de organizaciones más grandes que trabajan en
su propia pila TLS en paralelo, esto no es cierto para todos.

El dominante peso pesado de código abierto, OpenSSL, por ejemplo, no tiene
ninguna API para esto. El plan para abordar esto parece ocurrir en su [PR 
8797](https://github.com/openssl/openssl/pull/8797) que pretende introducir una
API muy similar a la de BoringSSL.

Esto eventualmente también conducirá a obstáculos en el despliegue, ya que las
pilas QUIC tendrán que basarse en otras bibliotecas TLS, utilizar una 
construcción separada de OpenSSL parcheada o requerir una actualización a una
futura versión de OpenSSL.

## Kernels y carga de la CPU

Tanto Google como Facebook han mencionado que sus despliegues a gran escala de
QUIC requieren aproximadamente el doble de CPU que la misma carga de tráfico
cuando se sirve HTTP/2 sobre TLS.

Algunas explicaciones para esto incluyen

- las partes UDP principalmente en Linux no están tan optimizadas como la pila
  TCP, ya que no se ha utilizado tradicionalmente para transferencias de alta
  velocidad como esta.

- la descarga de TCP y TLS al hardware existe, pero eso es mucho más raro para
  UDP y básicamente inexistente para QUIC.

Hay razones para creer que el rendimiento y los requisitos de la CPU mejorarán
con el tiempo.
