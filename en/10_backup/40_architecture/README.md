[//]: # (Reviewed and added by @Ali)

# Architecture
## Context
The described backup / restore process is limited to the application and log data. For a complete recovery, restoration at the hardware, operating system and application level must also be considered (elsewhere).

## Decisions
### Data transport by the pull method.
Backups are obtained from the drop system in the pull process. This decision has the following reasons:
* Security: If a single application is corrupted, the backup data is secure. The attacker finds no credentials for subsequent backup systems.
* Network access: backups must be stored "outside" to protect against the different risks. "Outside" also means outside of the network zones. In order to avoid exposing the centralized backup memories, data transports are therefore always triggered by the more centralized system.

### To do
* Authorization
* test
* Notification