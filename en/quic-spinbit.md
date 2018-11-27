# Spin Bit

One of the perhaps longest design discussions within the QUIC working group
that has been the subject of several hundred mails and hours of discussions
concerns a single bit: the Spin Bit.

The proponents of this bit insist that there is a need for operators and
people on the path between two QUIC endpoints to be able to measure latency.

The opponents to this feature do not like the potential information leak.

## Spinning a bit

Both endpoints, the client and the server, maintain a spin value, 0 or 1, for
each QUIC connection, and they set the spin bit on packets it sends for that
connection to the appropriate value.

Both sides then send out packets with that spin bit set to the same value
for as long as one round trip lasts and then it toggles the value. The effect
is then a pulse of ones and zeroes in that bitfield that observers can
monitor.

This measuring only works when the sender is neither application nor flow
control limited and packet reordering over the network can also make the data
noisy.
