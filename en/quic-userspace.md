## User-space

Implementing a transport protocol in user-space helps enable quick 
iteration of the protocol, as it is comparatively easy to evolve the 
protocol without necessitating that clients and servers update their 
operating system kernel to deploy new versions.

Nothing inherent in QUIC prevents it from being implemented and offered
by operating system kernels in the future, should someone find that a
good idea.

### Many implementations

One obvious effect of implementing a new transport protocol in 
user-space is that we can expect to see many independent implementations. 

Different applications are likely to include (or layer atop) different 
HTTP/3 and QUIC implementations for the foreseeable future.
