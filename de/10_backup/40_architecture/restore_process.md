# Schritte des Restore-Prozesses 

![the restore process][restore process]

[restore process]: https://raw.githubusercontent.com/DomainDrivenArchitecture/ddaArchitecture/ali/images/10_backup/restore_phases.png "the restore process"

## Datentransport zum Restore (1)
1. Quellen zur Wiederherstellung können entweder 
  1. das remote System (dataBackupSink (1.a))
  2. oder der Backup eines hosting providers (1.b)
2. Der Zugriff zu dem System, das wiederhergestellt werden soll, muss manuell erfolgen.
3. Backups, die wieder hergestellt werden sollen, müssen in /home/dataBackupSource/restore abgelegt werden. Das Restore-Skript verwendet das neueste verfügbare Backup im Restore-Verzeichnis.

## Restore (2)
Der Wiederherstellungsschritt ist applikations-individuell.