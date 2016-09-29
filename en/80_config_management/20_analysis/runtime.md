# Runtime
## How should configuration be distributed to the target systems?
Configuration can be distributed in push mode and pull mode.
* Push is important for security reason (server-credentials may not reside on every server node in net)
* Pull is important for social & technical reasons.
  * Technical: Some networks may be not accessible from outside.
  * Social: Developers don't like uncontrolled updates from outside.

## How we can express dependencies without knowing the target system ids?
We will be forced to express dependencies between target system parts. These dependencies has to exist prior to their applicatin to real target systems. So we will be forced to operate in our own key space, called the Specification Key Space. Keys from the Specification Key Space has to be mapped to target keys on creating the target systems.   

## Whats our strategy to handle large files?
TBD