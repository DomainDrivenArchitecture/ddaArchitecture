# Backup Sink
## Sink System Principles
 1. Procedure
   1. The backups are pulled from the source systems and stored in an input transport directory
   2. After the transport steps are triggered by the "Sink" system:
     1. Verification of successful transport.
     2. Perform the "source" system steps after transport.
     3. Perform the "Sink" system steps after transport.
       1. Move the backup files to the store
       2. (Optional) Execute evaluation after expiry
 2. Access
   1. The backup data and the backup log are pulled from different users:
     1. dataBackupSink
     2. logBackupSink
   2. the sink users have to be authorized at the source user,
   3. the sink user is managed by /home/[sinkUserName]/.ssh/authorized_keys.

## Transport incoming Folder
 1. Folder name
   1. transport-incoming
   2. \source-systems-dns-name
 2. File name
   1. as named on source system
 3. Example
   1. transport-incoming/owncloud.example.org/dda-owncloud_meissa_mysql_2015-01-28_04-52-01.sql

## Backup Store Folder
 1. Folder name
   1. store
   2. \[source-systems-dns-name]
   3. \[generation store] (e.g. daily | weekly | monthly)
 2. File name as described in "Transport incoming Folder"
 3. Example:
   1. store/owncloud.example.org/daily/dda-owncloud_meissa_mysql_2015-01-28_04-52-01.sql
