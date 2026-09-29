# Aster — Architecture

Aster consists of field sensors and a gateway responsible for receiving and forwarding observations.

Sensors produce timestamped environmental observations.

When connectivity is available, observations are transmitted according to the configured transmission interval.

When connectivity is unavailable, observations remain in local buffering.

After connectivity returns, buffered observations may be transmitted in batches.

Batch transmission changes how observations are transported. It does not change when those observations were originally measured.

The gateway receives both normal and delayed observations through the same observation format.
