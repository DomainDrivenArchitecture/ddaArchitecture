## 10_backup
### 20_analysis
* adjust to Michaels changes in de folder on backup-branch
* delete files which are not present on de and on back-up branch anymore

## 30_requirements
* req0096 Vom Backup gesicherte Datentypen -> adust this to german version
* I think we need to completly translate the german version to the correct englisch requirements
* Copy structure from german and check if aquivalent requirement is present in english, if not add it
  to the requirements and use it with include git. Watch out for requirement numbering

## 40_architecture
### README.md
* The described backup / restore process is limited to the application and log data.
  -> The described backup / restore process is limited to the application- and log data.
* For a complete recovery we have to consider the restoration on hardware, operating System,
 application and configuration level in another place as well.

 ### backup_process.md
* In the backup step, a cronjob is responsible for the "source" -> "source"-system
* 5. the "previous transport has failed" case and, e.g. To send an error mail. ->
  5. To handle the "previous transport has failed" case and e.g. send an Error-Mail.
* Do the Transport (2.a) -> Do the transport - in push-mode
* In the transport step, a sink system cron job will
  -> In the transport step, a cron-job on the "source"-system is responsible for
* Michael made some changes here, like removing ssh and rsync as we might switch to duplicity,
  i think you need to translate: Do the transport again to adjust to Michaels changes
* From the german version in the backup-branch, i think you are missing:
  -> Alternativ: Den Transport durchführen - im Pull-Mode (2.a)
* remove hosteurope

### restore_process.md
* remove picture
* change Restore Data Transport (1) -> Data transport to restore
* the dataBackupSink (1.a) -> add the remote system (dataBackupSink (1.a))

* delete files which are no longer present on backup de
