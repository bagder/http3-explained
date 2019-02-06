## IETF

The QUIC working group that was established to standardize the protocol within
the IETF quickly decided that the QUIC protocol should be able to transfer 
other protocols than "just" HTTP. Google-QUIC only ever transported HTTP - 
in practice it transported what was effectively HTTP/2 frames, using the 
HTTP/2 frame syntax.

It was also stated that IETF-QUIC should base its encryption and security on
TLS 1.3 instead of the "custom" approach used by Google-QUIC.

In order to satisfy the send-more-than-HTTP demand, the IETF QUIC protocol
architecture was split in two separate layers: the transport QUIC and the
"HTTP over QUIC" layer (the latter sometimes referred to as "hq").

This layer split, while it may sound innocuous, has caused the IETF-QUIC to
differ quite a lot from the original Google-QUIC.

The working group did however soon decide that in order to get the proper focus
and ability to deliver QUIC version 1 on time, it would focus on delivering
HTTP, leaving non-HTTP transports to later work.

In March 2018 when we started working on this book, the plan was to ship the
final specification for QUIC version 1 in November 2018; this was later
postponed to July 2019.

While the work on IETF-QUIC has progressed, the Google team has incorporated
details from the IETF version and has started to slowly progress their version
of the protocol towards what the IETF version might become. Google has continued
using their version of QUIC in their browser and services.

[Most new implementations under development](https://github.com/quicwg/base-drafts/wiki/Implementations)
have decided to focus on the IETF version and are not compatible with the Google version.
