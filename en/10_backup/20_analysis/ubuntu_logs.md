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