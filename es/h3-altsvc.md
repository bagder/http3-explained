# Alt-svc

La cabecera de servicio alternativo (Alt-svc:) y su correspondiente trama
`ALT-SVC` HTTP/2 no han sido creadas específicamente para QUIC o HTTP/3. Son
parte de un mecanismo ya diseñado y creado para que un servidor le diga a un
cliente: *"mira, ejecuto el mismo servicio en ESTE HOST usando ESTE PROTOCOLO
en ESTE PUERTO "*. Vea los detalles en [RFC 
7838](https://tools.ietf.org/html/rfc7838).

Un cliente que reciba tal respuesta Alt-svc es entonces aconsejado para, si lo
soporta y lo desea, conectarse a ese otro host en paralelo en segundo plano -
usando el protocolo especificado - y si tiene éxito cambiar sus operaciones a
eso en lugar de la conexión inicial.

Si la conexión inicial utiliza HTTP/2 o incluso HTTP/1, el servidor puede
responder e indicar al cliente que puede volver a conectarse e intentar HTTP/3.
Puede ser al mismo host o a otro que sepa servir ese origen. La información
dada en una respuesta Alt-svc de este tipo tiene un temporizador de caducidad,
lo que hace que los clientes puedan dirigir las siguientes conexiones y
peticiones directamente al host alternativo utilizando el protocolo alternativo
sugerido, durante un determinado periodo de tiempo.

## Ejemplo

Un servidor HTTP incluye una cabecera `Alt-Svc:` en su respuesta:

    Alt-Svc: h3=":50781"

Esto indica que HTTP/3 está disponible en el puerto UDP 50781 en el mismo nombre
de host que se utilizó para obtener esta respuesta.

Un cliente puede entonces intentar establecer una conexión QUIC con ese destino
y, si tiene éxito, seguir comunicándose con el origen así en lugar de con la
versión HTTP inicial.
