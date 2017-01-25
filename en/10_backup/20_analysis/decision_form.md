# Backup Decision Form
## General Decision Criteria
When we think about backing up our data the following aspects could be relevant:
* system configuration: configuration and installation state of the target system
* application configuration: the settings of the actual application
* application binaries: the executable files of the application
* application data: data that is created by the usage of the application
* log data: log messages which protocols important occurrences

### Data Types  to Backup
We backup application data and log data.
* System configuration
* Application configuration
* Application binaries
Code and configuration needs no backup, because code is saved by Version Management System.
 * Application Data
 * Log Data: Log files are synchronized daily. Storage duration is: e.g. 1 year
 * Security Log Data: Security logs need no backup, because they are synchronized in real time. Storage duration is:	e.g. 1 year

### Availability
 * **High**: Highly important data are stored on another computing center.
 * **Normal**: Normally important data are stored on another server.
 * **Low**: Less important data are stored only on the same server and on the hosting provider's backup store.

## Decisions and Analysis per Application
|ID|Measurement|
|--|--|
|**Application name**||
|Current application data size||
|Estimated application data growth for upcoming year||
|Log data growth / year||
|**App data backup on SourceSystem**||
|Generations in daily interval||
|Generations in weekly interval||
|Generations in monthly interval||
|**App data backup on SinkSystem**||
|Generations in daily interval||
|Generations in weekly interval||
|Generations in monthly interval||
|**Application needs**||
|App data importance / availability||
|App data confidentiality||
|Log data confidentiality||
|Time for disaster recovery||
