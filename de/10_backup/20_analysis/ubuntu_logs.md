# Besonderheiten beim Backup von Logfiles 
## Weiterführende Analysemöglichkeiten mit Log Backups
Dieses Backup ermöglicht etwas speziellere Analytik. Die Logfiles können zum Beispiel auf nicht autorisierte Änderungen analysiert werden und so einen weiteren Indikator für Angriffe liefern.

## Log-Daten Behandlung mit ubuntu12.04

|Aktueller Name	|Häufigkeit	|Komprimierung	|Generationen	|Unkomprimierter Name	|
| ------------- |-----------| --------- 	| ------------- | ----------------- 	|
|auth.log		|2d			|1+				|6				|auth.log.0				|
|syslog			|1d			|1+				|6				|syslog.0				|
|apache*		|1w			|1+				|52				|access.log.1			|
|catalina.out	|1w			|0+				|52				|--						|