# Special features when backing up logfiles
### Further Analysis Options on Log Backups
Backup allows some special analytics, for example log files can be analyzed for not authorized changes, thus providing a further indicator of attacks.

### Log Data handling on Ubuntu 12.04

|Current Name	|Frequency	|Compress	|Generations	|Uncompressed Name	|
| ------------- |-----------| --------- | ------------- | ----------------- |
|Auth.log		|2d			|1+			|6				|Auth.log.0			|
|Syslog			|1d			|1+			|6				|Syslog.0			|
|Apache*		|1w			|1+			|52				|access.log.1		|
|Catalina.out	|1w			|0+			|52				|--					|