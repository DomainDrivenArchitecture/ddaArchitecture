# Backup Sink
## Sink System Principles
 1  Process
   1  The backups are pulled from the source systems and stored to a transport incoming folder
   2  After the transport steps are triggered from the sink system:
     1  Check successful transport.
     2  Execute the source systems after the transport steps.
     3  Execute the sink systems after the transport steps.
       1  Rotate backup files
       2  Do after process analysis
 2  Access
   1  The backup data and the backup log are pulled from different users:
     1  dataBackupSink
     2  logBackupSink
   2   the sink users have to be authorized at the source user,
   3  the sink user is managed by /home/[sinkUserName]/.ssh/authorized_keys.

## Transport incoming Folder
 1  Folder-name
   1  transport-incoming
   2  \source-systems-dns-name
 2  File-name
   1  as named on source system
 3  Example
   1  transport-incoming/owncloud.example.org/dda-owncloud_meissa_mysql_2015-01-28_04-52-01.sql

## Backup Store Folder
 1  Folder-name
   1  store
   2  \[source-systems-dns-name]
   3  \[generation store] (e.g. daily | weekly | monthly)
 2  File-name as described in 4.4.2  Transport incoming Folder
 3  Example:
   1  store/owncloud.example.org/daily/dda-owncloud_meissa_mysql_2015-01-28_04-52-01.sql