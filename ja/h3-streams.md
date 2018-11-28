# QUIC streams and HTTP/3

HTTP/3 is made for QUIC so it takes full advantage of QUIC's streams, where
HTTP/2 had to design its entire stream and multiplexing concept of its own on
top of TCP.

HTTP requests done over HTTP/3 use a specific set of streams.

## HTTP/3 frames

HTTP/3 means setting up QUIC streams and sending over a set of frames to the
other end. There's but a small fixed number (eight!) of known frames in
HTTP/3. The most important ones are probably:

- HEADERS, that sends compressed HTTP headers
- DATA, sends binary data contents
- GOAWAY, please shutdown this connection

## HTTP Request

The client sends its HTTP request on a client-initiated *bidirectional* QUIC
stream.

A request consists of a single HEADERS frame and might optionally be followed
by one or two other frames: a series of DATA frames and possibly a final
HEADERS frame for trailers.

After sending a request, a client closes the stream for sending.

## HTTP Response

The server sends back its HTTP response on the bidirectional stream. A HEADERS
frame, a series of DATA frames and possibly a trailing HEADERS frame.

## QPACK headers

The HEADERS frames contain HTTP headers compressed using the QPACK algorithm.
QPACK is similar in style to the HTTP/2 compression called HPACK ([RFC
7541](https://httpwg.org/specs/rfc7541.html)), but modified to work with
streams delivered out of order.

QPACK itself uses two additional unidirectional QUIC streams between the two
end-points. They are used to carry dynamic table information in either
direction.
