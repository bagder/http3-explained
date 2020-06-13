## Experience from HTTP/2

The HTTP/2 specification RFC 7540 was published in May 2015, just a month
before QUIC was brought to IETF for the first time.

With HTTP/2, the foundation for changing HTTP over the wire was laid out and
the working group that created HTTP/2 was already of the mindset that this
would help iterating to new HTTP versions much faster than it had taken to go
to version 2 from version 1 (about 16 years).

With HTTP/2, users and software stacks got used to the idea that HTTP can no
longer be assumed to be done with a text-based protocol in a serial manner.

HTTP-over-QUIC (HTTP/3) builds upon HTTP/2 and follows many of the same concepts
but moves some of the specifics from the HTTP layer as they are covered by QUIC.