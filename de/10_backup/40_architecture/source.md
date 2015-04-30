# Backup Quelle
Auf Knoten, die als Backup Quelle dienen, gibt es zwei Backup-User, die dataBackupSource und logBackupSource heißen.

## Grundsätze des „Source“-Systems 
 1. Die Backups werden per pull vom „Source“-System bezogen.
 2. Ablauf
   1. Die Dateien des aktuellen Tages werden für den ausgehenden Transport zum „Backup Sink System“ vorgehalten.
   2. Nach dem erfolgreichen Transport werden die Dateien schließlich zu einem lokalen Speicherordner verschoben.
 3. Zugriff
   1. Die Backupdaten und das Backup-Log gehören unterschiedlichen Benutzern:
     1. dataBackupSource
     2. logBackupSource
   2. Der Zugriff zu den Backup Source Benutzern ist verwaltet durch /home/[sourceUserName]/.ssh/authorized_keys.

## Ausgehendes Transportverzeichnis
 1. Verzeichnisname: 
   1. transport-outgoing
 2. Dateiname: 
   1. [Anwendungsname]
   2. [Backup Source Variante] (z.B. Dateisystem | MySql)
   3. Zeitstempel
 3. Beispiel:
   1. transport-outgoing/dda-owncloud_meissa_mysql_2015-01-28_04-52-01.sql

## Lokales Backup Speicherverzeichnis
 1. Verzeichnisname
   1. store
 2. Dateiname (analog zu Abschnitt "Ausgehendes Transportverzeichnis")