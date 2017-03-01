# Backup Decision Form
## General Decision Criteria
When we think about backing up our data the following aspects could be relevant:
* System configuration: configuration and installation state of the target system
* Application configuration: the settings of the actual application
* Application binaries: the executable files of the application
* Application data: data that is created by the usage of the application
* Log data: log messages which protocols important occurrences

## Decisions criteria per Application
In addition to the actual backup contents (for which backup general guidelines
can apply), the individual application must also be considered:

|ID 								| Measurement |
|-- 								|--| 
|Application name 					|| 
|Current application data size			|| 
|Estimated application data growth for upcoming year || 
|Log data growth / year				|| 
|Application data backup on "Source" System		|| 
|Generations in daily interval		|| 
|Generations in weekly interval		||
|Generations in monthly interval	||
|Application data backup on the "Sink" System 	||
|Generations in daily interval		||
|Generations in weekly interval		|| 
|Generations in monthly interval	||
|Application requirements 			||
|Importance / availability of Application data	||
|Confidentiality of application data||
|Confidentiality of log data		||
|Recovery time from failure|||

# Decision example for the "sample company"
## As a general rule
We make a backup for application data and log data.
Code and configurations do not need backup because the code is stored in the version management system.
* ** System configuration: ** Is fully created by ConfigManagement and is therefore always reproducible. - No need for backup.
* ** Application configuration: ** Is completely created by ConfigManagement and is therefore always reproducible. - No need for backup.
* ** Application binaries: ** Binaries are stored for ConfigManagement on a special artifact server. - No additional backup required, general storage time: 1 year.
* ** Application data: ** Backed up according to criteria table - Backup requirements.
* ** Log data: ** Log data is partly aggregated and collected in real time (Logstash, Ossec). Log data is to be additionally saved for an in-depth analysis. Log data is thus saved according to the criteria table - backup requirement, general retention time: 1 year.

## Per application
For the definition of the application-specific requirements we have the above mentioned Table. For availability, we use the following definition:

** Definition Availability **
* High: Highly important data is stored in another data center.
* Normal: Normal important data is stored on another server.
* Low: Less important data is kept only on the same server and on the host provider's backup store.