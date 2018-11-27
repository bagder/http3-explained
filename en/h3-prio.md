# HTTP/3 Prioritization

One of the HTTP/3 stream frames is called `PRIORITY`. It is used to set
priority and dependency on a stream in a way very similar to how it works in
HTTP/2.

The frame can set a specific stream to depend on another specific stream and
it can set a "weight" on a given stream.

A dependent stream should only be allocated resources if either all of the
streams that it depends on are closed or it is not possible to make progress
on them.

A stream weight is value between 1 and 256 and it is specified that streams
with the same parent **should** be allocated resources proportionally based on
their weight.
