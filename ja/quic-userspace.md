## User-space

Implementing a transport protocol in user-space helped driving the development
and the quick iterations of the protocol since it was "easy" for Google to run
it in both ends of their operations and have users take advantage of new
development very frequently.

There is nothing that prevents this protocol from being implemented and
offered by operating system kernels in a future, should someone find that a
good idea.

### Many implementations

One obvious effect of implementing a new transport protocol that primarily
lives in user-space is that we see many independent implementations and we can
look forward to applications running with this rather big and complicated
transport protocol stack in them going forward and different applications using
different not only HTTP/3 but also QUIC stacks. It will for sure bring new
challenges.
