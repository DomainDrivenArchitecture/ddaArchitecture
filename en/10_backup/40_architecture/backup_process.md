# Backup Process Steps

![the backup process][backup process]

[backup process]: backup_phases.png "the backup process"

[//]: # (The translation contains 3 parts, however, it has 6 part originally: by @Ali, What should I do?)

## Backup Source
### Backing up (1)

In the backup step, a cronjob is responsible for the "source"
1. to stop the running application server (1.a).
2. Collect all application data (1.b) and log data (1.d).
3. restart the application server (1.c).
4. Transfer the collected data to the "Transport Handover Point".
5. the "previous transport has failed" case and, e.g. To send an error mail.

## Backup Data Transport (2)
### Do the Transport (2.a)
In the transport step, a sink system cron job will
1. do the transport (2.a): using ssh and rsync. For ssh, the sink system is authorized on dataBackupSource user.
2. (Optional) verify correctness: Done by hash comparison.
3. move to Sink-Store (2.b): Moves the received backup to Sink-Store.
4. handle Sink generations: Deletes the deepest backup up to the number of the defined generations to be preserved.
5. move to Source-Store (2.c): Moves the received backup to Source-Store.
6. handle Source Generations: Deletes backups, bailing out of the defined generations to be preserved.

## Backup Log Transport (3)
In the transport step, a sink system cron job will
1. do the transport (3.a): using ssh and rsync. For ssh, the sink system is authorized on logBackupSource user.
2. (Optional) verify correctness: Done by hash comparison
3. move to Sink-Store (3.b): Moves the received backup to Sink-Store
4. handle Sink generations: Deletes the deepest backup of the defined generations to be preserved.

## Use HostEurope Backup (4)
HostEurope backs up the whole file system of the last 14 days. If we just store one daily generation on the local file system, we have the ability to rollback to one of the last 14 days.
