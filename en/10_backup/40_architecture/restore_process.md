# Restore Process Steps

![the restore process][restore process]

[restore process]: https://raw.githubusercontent.com/DomainDrivenArchitecture/ddaArchitecture/ali/images/10_backup/restore_phases.png "the restore process"


## Restore Data Transport (1)
1. Source for restores can either be
  1. the dataBackupSink (1.a)
  2. or the backup from a hosting provider (1.b)
2. Access to the system being restored has to be assigned manually.
3. Backups to be restored, have to be placed in /home/dataBackupSource/restore. The restore script will take the latest backup available in the restore folder.

## Restore (2)
The restore step is part of the system applications individual procedures.

This is a test.