#Specific Environments
## Specialties at Log File Backup
### Further Analysis Options on Log Backups
Backup allows some special analytics, for example log files can be analyzed for not authorized changes.

### Log Data handling on ubuntu12.04
Some examples out of our experience: 

|Current Name	|Frequency	|Compress	|Generations	|Uncompressed Name	|
| ------------- |-----------| --------- | ------------- | ----------------- |
|auth.log		|2d			|1+			|6				|auth.log.0			|
|syslog			|1d			|1+			|6				|syslog.0			|
|apache*		|1w			|1+			|52				|access.log.1		|
|catalina.out	|1w			|0+			|52				|--					|

## Specialties at HostEurope
The Example Company is hosted at HostEurope. According to HostEurope product specification, the Example Company has the following backup (options) available:
* Snapshot: stores the whole server (application, configuration, data) – the recovery takes about 2-5h. The snapshots are stored for three months.
* Permanent Snapshot: Like snapshots, but with unlimited storage duration.
* File system backup: On daily backup basis, stored of the last 14 days.
