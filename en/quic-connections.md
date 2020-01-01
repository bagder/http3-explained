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
addressing at lower protocol layers (UDP, IP, and below) do not cause packets
for a QUIC connection to be delivered to the wrong endpoint. 

By taking advantage of the connection ID, connections can thus migrate between
IP addresses and network interfaces in ways TCP never could. For instance, 
migration allows an in-progress download to move from a cellular network connection
to a faster wifi connection when the user moves their device into a location 
offering wifi. Similarly, the download can proceed over the cellular connection
if wifi becomes unavailable.

## Port numbers

QUIC is built atop UDP, so a 16 bit port number field is used to differentiate
incoming connections.

## Version negotiation

A QUIC connection request originating from a client will tell the server
which QUIC protocol version it wants to speak, and the server will respond
with a list of supported versions for the client to select from.
