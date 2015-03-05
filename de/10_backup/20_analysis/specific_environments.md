# Besonderheiten beim Backup von Logfiles 
## Weiterführende Analyse Möglichkeiten mit Log Backups
Das Backup ermöglicht etwas speziellere Analytik. Die Logfiles können zum Beispiel auf nicht autorisierte Änderungen analysiert werden und so einen weiteren Indikator für Angriffe liefern.

## Log-Daten Behandlung mit ubuntu12.04

|Aktueller Name	|Häufigkeit	|Komprimierung	|Generationen	|Unkomprimierter Name	|
| ------------- |-----------| --------- 	| ------------- | ----------------- 	|
|auth.log		|2d			|1+				|6				|auth.log.0				|
|syslog			|1d			|1+				|6				|syslog.0				|
|apache*		|1w			|1+				|52				|access.log.1			|
|catalina.out	|1w			|0+				|52				|--						|

# Besonderheiten bei HostEurope
Das Beispiel Unternehmen hat seine Server  bei HostEurope gehostet. Nach der HostEurope Produktbeschreibung sind für das Beispiel Unternehmen die folgenden Backup Optionen verfügbar:
Snapshot: verwahrt den ganzen Server (Anwendung, Konfiguration, Daten) – die Wiederherstellung dauert ca. 2-5 Stunden. Die Snapshots werden drei Monate lang aufbewahrt.
Permanenter Snapshot: Vergleichbar mit Snapshots, nur mit unbegrenzter Aufbewahrungszeit.
File-System Backup: auf Basis eines täglichen Backups, wird für die letzten 14 Tage aufbewahrt.