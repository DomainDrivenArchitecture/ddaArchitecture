# Backup Decision Form

## Global Decisions
### Data Types  to Backup
We backup application data and log data.
Code and configuration needs no backup, because code is saved by Version Management System.
 * Application Data
 * Log Data: Logfiles are synchronized daily. Storage duration is: e.g. 1 Year
 * Security Log Data: Security logs need no backup, because they're synchronized in real time. Storage duration is:	e.g. 1 Year

### Availability
 * High: High important data are stored on another computing center.
 * Normal: Normal important data are stored on another server.
 * Low: Low important data are stored only on the same server and on the hosting providers backup store.

## Decisions and Analysis per Application
|ID|Measurement|
|--|--|
|Application name||
|Current application data size||
|Estimated application data growth for upcoming year||
|Log data growth / year||
|App data backup on SourceSystem||
|Generations in daily interval||
|Generations in weekly interval||
|Generations in monthly interval||
|App data backup on SinkSystem||
|Generations in daily interval||
|Generations in weekly interval||
|Generations in monthly interval||
|Application needs||
|App data importance / availability||
|App data confidentiality||
|Log data confidentiality||
|Time for disaster recovery||