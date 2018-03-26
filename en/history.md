# History

The initial QUIC protocol was designed by Jim Roskind at Google and was
initially implemented in 2012, announced publicly to the world in 2013 when
Google's experimentations broadened.

Google implemented the protocol and subequently deployed it both in their
widely used browser (Chrome) and in their widely used server-side services
(Google search, gmail, youtube and more). They iterated protocol versions
fairly quickly and over time they proved the concept to work reliably for a
vast portion of users.

In June 2015, the first internet draft for QUIC was sent to the IETF for
standardization, but it it took until late 2016 for a quic working group to
get approved and started. But then it took off immediately with a high degree
of interest from many parties.

In 2017, numbers quoted by QUIC engineers at Google mentioned that around 7%
of *all* Internet traffic were already using this protocol. The Google version
of the protocol that is.

## IETF

When the protocol standardization was taken to the IETF and a quic work group
was created, there were initial decisions made that the QUIC protocol that the
IETF was about to standardize should be able to transfer other protocols than
"just" HTTP. Google-QUIC only ever transported HTTP - in practice it
transported what was effectively HTTP/2 frames, using the HTTP/2 frame syntax.

It was also stated that IETF-QUIC should base its encryption and security on
TLS 1.3 instead of the "custom" approach used by Google-QUIC.

In order to satisfy the send-more-than-HTTP demand, the IETF QUIC protocol
architecture was split in two separate layers: the transport QUIC and the
"HTTP over QUIC" layer (the latter sometimes referred to as "hq").

This layer split, while it may sound innocuous, has caused the IETF-QUIC to
differ quite a lot from the original Google-QUIC.

The work group did however soon decide that in order to get the proper focus
and ability to deliver QUIC version 1 on time, it would focus on delivering
HTTP, leaving non-HTTP transports to later work.

At the time of this writing (March 2018), the plan is to ship the final
specification for QUIC version 1 around November 2018.

While the work on IETF-QUIC has progressed, the Google team has incorporated
details from the IETF version and has started to slowly progress their version
of the protocol towards what the IETF version might become. Google has keept
up running their version of QUIC in their browser and services.

Most new implementations that are in the works (*link to the the
implementations*) have decided to focus on the IETF version and are not
compatible with the Google version.
