# Runtime
## How should configuration be distributed to target systems?
Configuration can be distributed in push mode and pull mode.
* Push is important for security reason (server-credentials may not reside on every server node in net)
* Pull is important for social & technical reasons.
  * Technical: Some networks may be not accessible from outside.
  * Social: Developers don't like uncontrolled updates from outside.

## Do we need state and how can state be managed?
## How can we distinguish debit configuration from actual configuration?
There will always be the situation of different versions of deployed software. Distinguishing between debit and actual. "Configuration" denominates the pursued debit, the actual state of server nodes we will name "Facts".

*scj: Ist das absichtlich der gleiche Text nochmal wie auf der Seite modularization?*

## How configuration defined becomes to configuration be ready to be applied to real nodes?
## What is the role of Configuration Management in a bare metal-, cloud- and container-world?
## How can we transport information generated during the configuration / installation process?
## How are credentials handled secure?
## Whats our strategy to handle large files?
## When should we choose to overwrite configuration?