# HTTP/3 Prioritization

The base HTTP/3 specification doesn't define prioritization itself. The HTTP/2
approach to prioritization has been deemed too complicated and is deprecated by
the latest revision of the HTTP/2 specification [RFC
9113](https://www.rfc-editor.org/rfc/rfc9113.html). A simpler alternative, the
Extensible Prioritization Scheme for HTTP ([RFC
9218](https://www.rfc-editor.org/rfc/rfc9218.html)), has been published
separately, which can be used in both HTTP/2 and HTTP/3.

In HTTP/3, priority signals are sent in the form of the Priority header field
and/or the PRIORITY_UPDATE frame sent on the HTTP/3 Control Stream. Servers can
act on these signals to schedule sending of HTTP response content.
[RFC
9218](https://www.rfc-editor.org/rfc/rfc9218.html) provides scheduling guidance
that is intended to improve client web application performance.
