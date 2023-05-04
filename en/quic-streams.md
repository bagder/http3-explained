# Streams

Streams in QUIC provide a lightweight, ordered byte-stream abstraction.

There are two basic types of stream in QUIC:

 - Unidirectional streams carry data in one direction: from the initiator of the stream to its peer.

 - Bidirectional streams allow for data to be sent in both directions.

Either type of stream can be created by either endpoint, can concurrently send
data interleaved with other streams, and can be canceled.

To send data over a QUIC connection, one or more streams are used.

## Flow control

Streams are individually flow controlled, allowing an endpoint to limit memory
commitment and to apply back pressure. The creation of streams is also flow
controlled, with each peer declaring the maximum stream ID it is willing to
accept at a given time.

## Stream Identifiers

Streams are identified by an unsigned 62-bit integer, referred to as the
Stream ID. The least significant two bits of the Stream ID are used to
identify the type of stream (unidirectional or bidirectional) and the
initiator of the stream.

The least significant bit (0x1) of the Stream ID identifies the initiator of
the stream. Clients initiate even-numbered streams (those with the least
significant bit set to 0); servers initiate odd-numbered streams (with the bit
set to 1).

The second least significant bit (0x2) of the Stream ID differentiates between
unidirectional streams and bidirectional streams. Unidirectional streams
always have this bit set to 1 and bidirectional streams have this bit set to
0.

## Stream concurrency

QUIC allows for an arbitrary number of streams to operate concurrently. An
endpoint limits the number of concurrently active incoming streams by limiting
the maximum stream ID.

The maximum stream ID is specific to each endpoint and applies only to the
peer that receives the setting.

## Sending and Receiving Data

Endpoints use streams to send and receive data. That is after all their
ultimate purpose. Streams are an ordered byte-stream abstraction. Separate
streams are however not necessarily delivered in the original order.

## Stream Prioritization

Stream multiplexing has a significant effect on application performance if
resources allocated to streams are correctly prioritized. Experience with
other multiplexed protocols, such as HTTP/2, shows that effective
prioritization strategies have a significant positive impact on performance.

QUIC itself does not provide signals for exchanging prioritization information.
Instead it relies on receiving priority information from the application that
uses QUIC. Protocols that use QUIC are able to define any prioritization
scheme that suits their application semantics.

The Extensible Prioritization Scheme for HTTP ([RFC
9218](https://www.rfc-editor.org/rfc/rfc9218.html)) can be used for HTTP/3. It
defines signals and provides scheduling guidance. This scheme is simpler than
the original one defined for HTTP/2.
