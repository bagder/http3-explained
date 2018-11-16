# Connections

A QUIC connection is a single conversation between two QUIC endpoints. QUIC's
connection establishment combines version negotiation with the cryptographic
and transport handshakes to reduce connection establishment latency.

To actually send data over such a connection, one or more streams have to be
created and used.

## Connection ID

Each connection possesses a set of connection identifiers, or connection IDs,
each of which can be used to identify the connection. Connection IDs are
independently selected by endpoints; each endpoint selects the connection IDs
that its peer uses.

The primary function of these connection IDs is to ensure that changes in
addressing at lower protocol layers (UDP, IP, and below) don't cause packets
for a QUIC connection to be delivered to the wrong endpoint. 

By taking advantage of the connection ID, connections can thus migrate between
IP addresses and network interfaces in ways TCP never could.
