# Status

The QUIC working group has worked fiercely since late 2016 on specifying the
protocols and is approaching final stages at the time of writing (June 2020).

During 2019 and 2020 there has been an increasing number of [interoperability
tests with HTTP/3](https://docs.google.com/spreadsheets/d/1D0tW89vOoaScs3IY9RGC0UesWGAwE6xyLk0l4JtvTVg)
and CDNs and Browsers have started launching initial support - though often
behind flags.

There are a number different [QUIC implementations
listed](https://github.com/quicwg/base-drafts/wiki/Implementations)
in the QUIC working groups' wiki pages.

Implementing QUIC is not easy and the protocol has kept moving and changing
even up to this date.

## Servers

NGINX support for QUIC and HTTP/3 is under development and a [preview version has been announced](https://www.nginx.com/blog/introducing-technology-preview-nginx-support-for-quic-http-3/).

There have been no public statement in terms of support for QUIC from Apache.

## Clients

None of the larger browser vendors have yet shipped any version, at any state,
that can run the IETF version of QUIC or HTTP/3.

Google Chrome has shipped with a working implementation of Google's own QUIC
version since many years and has recently started supporting the IETF version behind a flag. Firefox similarly supports this behind a flag.

curl shipped the first experimental HTTP/3 support (draft-22) in the 7.66.0
release on September 11, 2019. curl uses either the Quiche library from
Cloudflare or the ngtcp2 family of libraries to get the work done.

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
API for this. The plan to address this seems to happen in their [PR
8797](https://github.com/openssl/openssl/pull/8797) that aims to introduce an
API that is very similar to the one of BoringSSL.

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
