# HTTP/3 Prioritization

As mentioned previously, priorisation between streams has been removed from the
main HTTP/3 specification to be worked on separately.

This was due learnings from the HTTP/2 prioritisation model and it's
implementation (or lack there of) in the real world.

A [simpler prioritisation model than HTTP/2 has been proposed](https://tools.ietf.org/html/draft-ietf-httpbis-priority)
using HTTP header fields with a limited number of priority settings. This is a
key change from the Dependency and Weight flags in the HTTP/2 Header frames and
allows better understanding at the application layer.

Reprioritisation, and whether to support this, is still being discussed. HTTP/2
had Prioritisation frames to handle this but the true independent streams in QUIC
and HTTP/3 makes this more complicated so the benefits versus the complexity are
still being debated.

When (or if!) a better prioritisation model is agreed for HTTP/3 it is hoped to
be able to backport this to HTTP/2 too, to address the complexity and
implementation concerns there.
