# Backup Sink
## Grundsätze des „Sink Systems“ 
 1. Ablauf
   1. Die Backups werden vom „Source“-System bezogen und in einem Eingangstransport-Verzeichnis gespeichert.
   2. Die Schritte nach dem Transport werden von dem „Sink“-System angestoßen:
     1. Überprüfung des erfolgreichen Transports.	
     2. Ausführen der „Source“-System-Schritte nach dem Transport.
     3. Ausführen der „Sink“-System-Schritte nach dem Transport.
       1. Verschieben der Backup-Dateien in den Store
       2. (Optional) Auswertung nach Ablauf durchführen
 2. Zugriff
   1. Die Backup-Daten und das Backup-Log werden von unterschiedlichen Usern bezogen:
     1. dataBackupSink
     2. logBackupSink
   2. Die „Sink“-Benutzer müssen für die „Source“-Benutzer berechtigt werden.
   3. Der „Sink“-Benutzer ist verwaltet durch /home/[sinkUserName]/.ssh/authorized_keys.

## Eingehendes Transportverzeichnis
 1. Verzeichnisname
   1. transport-incoming
   2. \source-systems-dns-name
 2. Dateiname
   1. analoge Benennung zum „Source“-System
 3. Beispiel
   1. transport-incoming/owncloud.example.org/dda-owncloud_meissa_mysql_2015-01-28_04-52-01.sql

## Backup Speicherordner
 1. Verzeichnisname
   1. store
   2. \[source-systems-dns-name]
   3. \[Speichergeneration] (z.B. täglich | wöchentlich | monatlich)
 2. Dateiname wie in Abschnitt "Eingehendes Transportverzeichnis" beschrieben
 3. Beispiel:
   1. store/owncloud.example.org/daily/dda-owncloud_meissa_mysql_2015-01-28_04-52-01.sql