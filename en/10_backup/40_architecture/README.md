# Architecture
## Context
The described backup / restore process is limited to the application- and log data. For a complete recovery we have to consider the restoration on hardware, operating System, application and configuration level in another place as well. 


## Decisions
### Data transport by the pull method.
Backups are obtained exclusively from the drop system in the pull process. This decision has the following reasons:
* Security: If a single application is corrupted, the backup data is secure. The attacker finds no credentials for subsequent backup systems.
* Network access: backups must be stored "outside" to protect against the different risks. "Outside" also means outside of the network zones. In order to avoid exposing the more centralized backup memories, data transports are therefore always triggered by the more centralized system.

### To do
* Authorization
* test
* Notification