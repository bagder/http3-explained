# HTTP/3 Server push

HTTP/3 server push is similar to what is described in HTTP/2 (RFC 7540), but
uses different mechanisms.

A server push is effectively the response to a request that the client never
sent!

Server pushes are only allowed to happen if the client side has agreed to
them. In HTTP/3 the client even sets a limit for how many pushes it accepts
but informing the server what the max push stream ID is. Going over that limit
will cause a connection error.

If the server deems it likely that the server wants an extra resource that it
hasn't asked for but ought to have anyway, it can send the client a
`PUSH_PROMISE` to the client (over the request stream) showing how the request
looks like that the push is sending a response to, and then send the response
over a new stream.

But even when pushes have been said to be acceptable by the client, each
individual pushed stream can still be canceled at any time if the client
deems that suitable. It then sends a `CANCEL_PUSH` frame to the server.

## Problematic

Ever since this feature was first discussed in the HTTP/2 development and
later after the protocol shipped and has been deployed over the Internet, this
feature has been discussed, disliked and pounded up in countless different
ways in order to get it to become useful.

Pushing is never "free", since while it saves a half round-trip it still uses
bandwidth. It is often hard or impossible for the server-side to actually know
with a high level a certainty if a resource should be pushed or not.
