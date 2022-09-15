# Cómo funciona QUIC

Sin explicar los bits y bytes exactos en el cable, esta sección describe cómo
funcionan los bloques fundamentales del protocolo de transporte QUIC. Si quieres
implementar tu propio stack QUIC, esta descripción debería darte una comprensión
general, pero para todos los detalles, consulta los actuales borradores de 
Internet del IETF y las RFC.

1. Configura una [conexión](quic-connections.md)
2. ... que incluya [seguridad TLS](quic-tls.md)
3. Luego utiliza [flujos](quic-streams.md)
