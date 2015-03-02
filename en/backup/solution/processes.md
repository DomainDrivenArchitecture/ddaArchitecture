# Backup Process Steps

![the backup process][backup process]
[backup process]: backup_phases.png "the backup process"

## Backup Source
### Backing up (1)
In the backup step, a source system cron job will 
1. collect all application (1.a) and log (1.b) data.
2. deliver this data to the “Transport Handover Point”
3. handle the “previous transport failed” case (send a mail).

## Backup Data Transport (2)
### Do the Transport (2.a)
In the transport step a sink system cron job will
1. do the transport (2.a): using ssh and rsync. For ssh, the sink system is authorized on dataBackupSource user.
2. (optional) verify correctness: Done by hash comparison.
3. move to Sink-Store (2.b): Moves the received backup to Sink-Store.
4. handle Sink generations: Deletes the eldest backup up to the number of the defined generations to be preserved.
5. move to Source-Store (2.c): Moves the received backup to Source-Store.
6. handle Source Generations: Deletes backups, bailing out of the defined generations to be preserved.

## Backup Log Transport (3)
In the transport step a sink system cron job will
1. do the transport (3.a): using ssh and rsync. For ssh, the sink system is authorized on logBackupSource user.
2. (optional) verify correctness: Done by hash comparison
3. move to Sink-Store (3.b): Moves the received backup to Sink-Store
4. handle Sink generations: Deletes the eldest backup of the defined generations to be preserved.

## Use HostEurope Backup (4)
HostEurope backs up the whole file system of the last 14 days. If we just store one daily generation on the local file system, we have the ability to rollback to one of the last 14 days.

# Restore Process Steps
![the restore process][restore process]
[restore process]: restore_phases.png "the restore process"

## Restore Data Transport (1)
1. Source for restores can either be
1. the dataBackupSink (1.a)
2. or the HostEurope Backup (1.b). How to get backuped files back is described at https://kis.hosteurope.de/support/faq/index.php?cpid=16063&in_object=40&searchword=backup
2. Access to the system being restored has to be assigned manually.
3. Backups to be restored, have to be placed in /home/dataBackupSource/restore. The restore script will take the newest backup available in the restore folder.

## Restore (2)
The restore step is part of the system applications' individual procedure.