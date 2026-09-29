# Aster — Requirements

Aster coordinates environmental measurements collected by distributed field sensors.

## Measurement Format

All measurements are stored using SI units.

## Observation Transmission

Under normal connectivity, each sensor submits observations every 10 minutes.

## Connectivity Loss

Sensors must continue recording observations when connectivity is unavailable.

Observations that cannot be transmitted must be buffered locally until transmission becomes possible again.

Buffered observations must retain their original measurement time.

## Data Retention

Aster must support the future introduction of a raw-data retention policy without requiring changes to the sensor measurement format.
