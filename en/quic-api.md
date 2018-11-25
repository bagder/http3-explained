# API

One of the success factors for regular TCP and programs using that, is the
standardized socket API. It has well defined functionality and using this API
you can move programs between many different operating systems as TCP works
the same.

QUIC is not there. There is no standard API for QUIC.

With QUIC, you need to pick one of the existing library implementations and
stick with its API. It makes applications "locked in" to a single library to
some extent. Changing to another library means another API and that might
involve a lot of work.

Also, since QUIC is typically implemented in user-space, it can't easily just
extend the socket API or appear similar to how existing TCP and UDP
functionality do. Using QUIC will mean using another API than the socket API.
