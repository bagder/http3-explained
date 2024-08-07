# QUIC future

In order to get the most focus possible on the core QUIC protocol and be able
to ship it on time, several features that were originally planned to be part
of the core protocol have been postponed and are now planned to instead get
done in a subsequent QUIC version.

The author of this document does however have a rather faulty crystal ball so
we can not tell for sure exactly what features will or will not appear in such
a future version. We can however mention some of the features and things that
explicitly have been removed from the v1 work to be "worked on later" and that
then possibly might appear in a future version.

## Forward Error Correction

Forward error correction (FEC) is a method of obtaining error control in data
transmission in which the transmitter sends redundant data and the receiver
recognizes only the portion of the data that contains no apparent errors.

Google experimented with this in their original QUIC work but it was
subsequently removed again since the experiments did not turn out well. This
feature is subject for discussion for QUIC but probably takes for someone to
prove that it actually can be a useful addition without too much penalty.

## Multipath

Multipath means that the transport can by itself use multiple network paths to
maximize resource usage and increase redundancy.

The SCTP proponents of the world like to mention that SCTP already features
multipath and so does modern TCP.

## Unreliable data

It has been discussed to offer "unreliable" streams as an option, that would
then allow QUIC to also replace UDP-style applications.

## Non-HTTP adaptions

DNS over QUIC was one of the early mentioned non-HTTP protocols that just
might get some attention once QUIC v1 and HTTP/3 ship. But with a new
transport like this having been brought on to the world I cannot imagine that
it will stop there.
