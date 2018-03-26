## Ossification

Changes to TCP also suffers from the middle-box problem, in that some of the
boxes will spot new TCP options and block such connections since they don't
know what the options are. That's called "protocol ossification". If allowed
to spot protocol details, systems learn how protocols behave and over time it
becomes impossible to change them.

The only truly effective way to "combat" ossification, is to encrypt as much
as possible of the communcation to prevent middle-boxes to see much of the
protocol passing through.
