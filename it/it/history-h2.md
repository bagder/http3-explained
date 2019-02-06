## Experience from HTTP/2

The HTTP/2 specification RFC 7540 was publiched in May 2015, just a month
before QUIC was brought to IETF for the first time.

With HTTP/2, the foundation for changing HTTP over the wire was laid out and
the working group that created HTTP/2 was already of the mindset that this
would help iterating to new HTTP versions much faster than it had taken to go
to version 2 from version 1 (about 16 years).

With HTTP/2, users and software stacks got used to the idea that HTTP can no
longer be assumed to be done with a text-based protocol in a serial manner.

QUIC and QUIC over HTTP are not "HTTP/3" in the name, but can very well be
seen like that in concept. Lots of experiences were done with HTTP/2 and the
web transport world has learned a great deal from deployments of that. Lessons
that have been brought into the QUIC work and are used there.
