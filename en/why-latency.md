# Earlier data

QUIC offers both 0-RTT and 1-RTT handshakes that reduce the time it takes to
negotiate and setup a new connection. Compare with the 3-way handshake of TCP.

In addition to that, QUIC offers "early data" support from the get-go which is
done to allow more data and it is used more easily than TCP Fast Open.

With the stream concept, another logical connection to the same host can be
done at once without having to wait for the existing one to end first.

## TCP Fast Open is problematic

TCP Fast Open was published as [RFC 7413](https://tools.ietf.org/html/rfc7413)
in December 2014 and that specification describes how applications can pass
data to the server to be delivered already in the first TCP SYN packet.

Actual support for this feature in the wild has taken time and is riddled with
problems even today in 2018. The TCP stack implementors have had issues and so
have applications trying to take advantage of this feature - both in knowing
in which OS version to try to activate it but also in figuring out how to
gracefully back down and deal when problems arise. Several networks have been
identified to interfere with TFO traffic and they have thus actively ruined
such TCP handshakes.
