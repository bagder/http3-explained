# Ossification

The internet is a network of networks. There is equipment set up on the
Internet in many different places along the way to make sure this network of
networks works as it is supposed to. These devices, the boxes that are
distributed out in the network, are what we sometimes refer to as middle-boxes.
Boxes that sit somewhere between the two end-points that are the primary parties
involved in a traditional network data transfer.

These boxes serve many different specific purposes but I think we can say that
universally they are put there because someone thinks they must be there to
make things work.

Middle-boxes route IP packets between networks, they block malicious traffic,
they do NAT (Network Address Translation), they improve performance, some try
to spy on the passing traffic and more.

In order to perform their duties these boxes must know about networking and
the protocols that are monitored or modified by them. They run software for
this purpose. Software that is not always upgraded frequently.

While they are glue components that keep the Internet together they are also
often not keeping up with the latest technology. The middle of the network
typically does not move as fast as the edges, as the clients and the servers of
the world.

The network protocols that these boxes might want to inspect, and have ideas
about what is okay and what is not then have this problem: these boxes were
deployed some time ago when the protocols had a feature set of that
time. Introducing new features or changes in behavior that were not known
before risks ending up considered bad or illegal by such boxes. Such traffic
may well just be dropped or delayed to the degree that users really do not
want to use those features.

This is called "protocol ossification".

Changes to TCP also suffer from ossification: some boxes between a client and
the remote server will spot unknown new TCP options and block such connections
since they do not know what the options are. If allowed to detect protocol
details, systems learn how protocols typically behave and over time it becomes
impossible to change them.

The only truly effective way to "combat" ossification is to encrypt as much of
the communication as possible in order to prevent middle-boxes from seeing much
of the protocol passing through.
