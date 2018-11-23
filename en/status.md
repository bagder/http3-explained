# Status

The QUIC working group has worked fiercely since late 2016 on specifying the
protocols and the plan is now to have it done by July 2019.

As of November 2018, there still hasn't been any larger interop tests with
HTTP/3 - only with the existing two implementations and none of them are done
by a browser or a popular open server software.

There are fifteen or so different QUIC implementations listed in the working
groups wiki pages, but far from all of them can interop on the latest spec
draft revisions.

Implementing QUIC is not easy and the protocol has kept moving and changing
even up to this date.

## Servers

There have been no public statement in terms of support for QUIC from Apache
or nginx.

## Clients

None of the larger browser vendors have yet shipped any version, at any state,
that can run the IETF version of QUIC or HTTP/3.

Google Chrome has shipped with a working implementation of Google's own QUIC
version since many years, but that doesn't interop with the official QUIC
protocol and its HTTP implementation is very different than HTTP/3.

## Kernels and CPU load

Both Google and Facebook have mentioned that their wide scale deployments of
QUIC require roughly twice the amount of CPU than the same traffic load does
when serving HTTP/2 over TLS.

Some explanations for this include

- the UDP parts in primarily Linux is not at all as optimized as the TCP stack
  is, since it has not traditionally been used for high speed transfers like
  this.

- TCP and TLS offloading to hardware exist, but that's much rarer for UDP and 
  basically non-existing for QUIC.

There are reasons to believe that performance and CPU requirements will
improve over time.
