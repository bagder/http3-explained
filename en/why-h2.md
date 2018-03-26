## Remember HTTP/2?

The HTTP/2 specification [RFC 7540](http://httpwg.org/specs/rfc7540.html) was
published in May 2015 and the protocol has since then been implemented and
deployed widely across the Internet and the world wide web.

In early 2018, almost 40% of the top-1000 web sites run HTTP/2, around 70% of
all HTTPS requests Firefox issues get HTTP/2 responses back and all major
browsers, servers and proxies support it.

HTTP/2 adresses a whole slew of shortcomings in HTTP/1 and with the
introduction of the second version of HTTP users can stop using a bunch of
work-arounds. Some of which are pretty burdonsome on web developers.

One of the primary features of HTTP/2 is that it makes use of multiplexing, so
that many logical streams are sent over the same physical TCP connection. This
makes a lot of things better and faster. It make congestion control work much
better, it let's users use TCP much better and thus properly saturate the
bandwidth, makes the TCP connections more long-lived - which is good so that
they get up to full speed more frequently than before. Header compression
makes it use less bandwidth.

With HTTP/2, browsers typically use *one* TCP connection to each host instead
of the previous *six*. In fact, connection coalescing and "desharding"
techniques used with HTTP/2 may actually even reduce the number of connections
much more than so.

With HTTP/2, the HTTP head of line blocking problem was "fixed". The problem
that clients had to wait for the request before in the line to finish before
the next one could go out.

