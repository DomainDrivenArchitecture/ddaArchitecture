# Restore Process Steps

![the restore process][restore process]

[restore process]: restore_phases.png "the restore process"

## Restore Data Transport (1)
1. Source for restores can either be
  1. the dataBackupSink (1.a)
  2. or the HostEurope Backup (1.b). How to get backuped files back is described at https://kis.hosteurope.de/support/faq/index.php?cpid=16063&in_object=40&searchword=backup
2. Access to the system being restored has to be assigned manually.
3. Backups to be restored, have to be placed in /home/dataBackupSource/restore. The restore script will take the latest backup available in the restore folder.

## Restore (2)
The restore step is part of the system applications individual procedures.