## Ossification

Changes to TCP also suffers from the middle-box problem: some boxes between a
client and the remote server will spot unknown new TCP options and block such
connections since they don't know what the options are. That is called
"protocol ossification". If allowed to detect protocol details, systems learn
how protocols typically behave and over time it becomes impossible to change
them.

The only truly effective way to "combat" ossification, is to encrypt as much
as possible of the communication to prevent middle-boxes to see much of the
protocol passing through.
