# Backup Process Steps

![the backup process][backup process]

[backup process]: /images/10_backup/backup_phases.png "the backup process"

## Backup Source
### Backing up (1)
In the backup step, a cronjob is responsible for the "source"-system
1. To stop the running application server (1.a).
2. Collect all application data (1.b) and log data (1.d).
3. Restart the application server (1.c).
4. Transfer the collected data to the "Transport Handover Point".
5. To handle the "previous transport has failed" case and e.g. send an Error-Mail.


## Backup Data Transport (2)
### Do the transport - in push-mode (2.a)
In the transport step, a cron-job on the "source"-system is responsible for
1. do the transport (2.a): The dataBackupSource User is authorized to store on the "Sink" system.
2. (Optional) verify correctness: By means of hash comparison.
3. Treat "sink" generations: Deletes the oldest backups, which exceed the selected number of backup generations to be kept.
4. Move to the "Source Store" (2.c): Moves the resulting backup to the "Source Store".
5. Treat Source Generations: Deletes backups according to the selected source system generations.

### Alternative: Carry out the transport - in pull mode (2.a)
In the transport step, a cron job is responsible for the "sink" system,
1. do the transport (2.a): The "Sink" system is authorized for the dataBackupSource user.
2. (optional) verify correctness: By means of hash comparison.
3. Move to the "Sink-Store" (2.b): Move the resulting backup to the "Sink-Store".
4. Treat "sink" generations: Deletes the oldest backups, which exceed the selected number of backup generations to be kept.
5. Move to the "Source Store" (2.c): Moves the resulting backup to the "Source Store".
6. Treat Source Generations: Deletes backups according to the selected source system generations.


## Backup Log Transport (3)
In the transport step, a cronjob of the "sink" system is responsible for
1. Do the transport (3.a): using ssh and rsync. For ssh, the sink system is authorized on logBackupSource user.
2. (Optional) verify correctness: Done by hash comparison
3. Move to Sink-Store (3.b): Moves the resulting backup to the Sink-Store
4. Handle Sink generations: Deletes the oldest backup of the defined generations to be preserved.