# HTTP/3 Server push

HTTP/3 server push is similar to what is described in HTTP/2 ([RFC
7540](https://httpwg.org/specs/rfc7540.html)), but uses different mechanisms.

A server push is effectively the response to a request that the client never
sent!

Server pushes are only allowed to happen if the client side has agreed to
them. In HTTP/3 the client even sets a limit for how many pushes it accepts
by informing the server what the max push stream ID is. Going over that limit
will cause a connection error.

If the server deems it likely that the client wants an extra resource that it
hasn't asked for but ought to have anyway, it can send a `PUSH_PROMISE` frame
(over the request stream) showing what the request looks like that the push is
a response to, and then send that actual response over a new stream.

Even when pushes have been said to be acceptable by the client before-hand,
each individual pushed stream can still be canceled at any time if the client
deems that suitable. It then sends a `CANCEL_PUSH` frame to the server.

## Problematic

Ever since this feature was first discussed in the HTTP/2 development and
later after the protocol shipped and has been deployed over the Internet, this
feature has been discussed, disliked and pounded up in countless different
ways in order to get it to become useful.

Pushing is never "free", since while it saves a half round-trip it still uses
bandwidth. It is often hard or impossible for the server-side to actually know
with a high level of certainty if a resource should be pushed or not.
