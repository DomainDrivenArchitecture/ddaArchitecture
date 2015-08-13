# Backup Source
On nodes serving as backup source, there are two backup users called dataBackupSource and logBackupSource.

## Source System Principles
 1. Backups are pulled from the source systems.
 2. Process
   1. The current day's files are held for transport-outgoing to the backup sink system.
   2. After successful transport, files are eventually moved to a local storage folder.
 3. Access
   1. The backup data and the backup log are owned by different users:
     1. dataBackupSource
     2. logBackupSource
   2. Access to the backup source users is managed by /home/[sourceUserName]/.ssh/authorized_keys.

## Transport outgoing Folder
 1. Folder name
   1. transport-outgoing
 2. File name
   1. [application name]
   2. [backup source type] (eg. file system | mysql)
   3. time stamp
 3. Example:
   1. transport-outgoing/dda-owncloud_meissa_mysql_2015-01-28_04-52-01.sql

## Local Backup Store Folder
 1. Folder name
   1. store
 2.File name (same as in 4.3.2  Transport outgoing Folder)
 