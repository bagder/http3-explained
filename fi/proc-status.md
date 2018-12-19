# Status

The QUIC working group has worked fiercely since late 2016 on specifying the
protocols and the plan is now to have it done by July 2019.

As of November 2018, there still has not been any larger interoperability
tests with HTTP/3 - only with the existing two implementations and none of
them are done by a browser or a popular open server software.

There are fifteen or so different [QUIC implementations
listed](https://github.com/curl/curl/wiki/QUIC-implementation) in the QUIC
working groups' wiki pages, but far from all of them can interoperate on the
latest spec draft revisions.

Implementing QUIC is not easy and the protocol has kept moving and changing
even up to this date.

## Servers

There have been no public statement in terms of support for QUIC from Apache
or nginx.

## Clients

None of the larger browser vendors have yet shipped any version, at any state,
that can run the IETF version of QUIC or HTTP/3.

Google Chrome has shipped with a working implementation of Google's own QUIC
version since many years, but that does not interoperate with the official
QUIC protocol and its HTTP implementation is different than HTTP/3.

## Implementation Obstacles

QUIC decided to use TLS 1.3 as the foundation for the crypto and security
layer to avoid inventing something new and instead lean on a trustworthy and
existing protocol. However, while doing this, the working group also decided
that to really streamline the use of TLS in QUIC, it should only use "TLS
messages" and not "TLS records" for the protocol.

This might sound like an innocuous change, but this has actually caused a
significant hurdle for many QUIC stack implementors. Existing TLS libraries
that support TLS 1.3 simply do not have APIs enough to expose this
functionality and allow QUIC to access it. While several QUIC implementors
come from larger organizations who work on their own TLS stack in parallel,
this is not true for everyone.

The dominant open source heavyweight OpenSSL for example, does not have any
API for this and has not expressed any desire to provide any such anytime soon
(as of November 2018).

This will eventually also lead to deployment obstacles since QUIC stacks will
need to either base themselves on other TLS libraries, use a separate patched
OpenSSL build or require an update to a future OpenSSL version.

## Kernels and CPU load

Both Google and Facebook have mentioned that their wide scale deployments of
QUIC require roughly twice the amount of CPU than the same traffic load does
when serving HTTP/2 over TLS.

Some explanations for this include

- the UDP parts in primarily Linux is not at all as optimized as the TCP stack
  is, since it has not traditionally been used for high speed transfers like
  this.

- TCP and TLS offloading to hardware exist, but that is much rarer for UDP and 
  basically non-existing for QUIC.

There are reasons to believe that performance and CPU requirements will
improve over time.
