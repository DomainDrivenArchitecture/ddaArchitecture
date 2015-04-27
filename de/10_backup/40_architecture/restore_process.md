# Schritte des Restore-Prozesses 

![the restore process][restore process]

[restore process]: restore_phases.png "the restore process"

## Datentransport zum Restore (1)
1. Quellen zur Wiederherstellung können entweder 
  1. das remote System (dataBackupSink (1.a))
  2. oder das HostEurope Backup (1.b) sein. Wie Backup-Files wieder zurückgeholt werden können, ist hier beschrieben: https://kis.hosteurope.de/support/faq/index.php?cpid=16063&in_object=40&searchword=backup
2. Der Zugriff zu dem System, das wiederhergestellt werden soll, muss manuell erfolgen.
3. Backups, die wieder hergestellt werden sollen, müssen in /home/dataBackupSource/restore abgelegt werden. Das Restore-Skript verwendet das neueste verfügbare Backup im Restore-Verzeichnis.

## Restore (2)
Der Wiederherstellungsschritt ist applikations-individuell.