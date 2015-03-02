# Anforderungsanalyse
##  Varianten von Backup Daten
1. Anwendungs-Code: Code für alle individuellen Anwendungs-Installationen.
2. Anwendungs-Daten: Daten der installierten und genutzten Anwendungen.
3. Konfiguration: Konfiguration der Komponenten oder Anwendungen.
4. Log Daten: Logfiles für alle laufenden Anwendungen.
5. Sicherheits-Log Daten: Für gesicherte Systeme gibt es spezielle Sicherheits-Logfiles.

##  Backup Daten Deduplizierung
Auch wenn es viele Zwischenvarianten gibt, werden wir hier nur nach den zwei Hauptvarianten unterscheiden:
1. Vollständiges Backup
2. Inkrementelles Backup
Aufgrund der kleinen Backup-Größe bei unserem Beispiel Unternehmen, werden wir nur das vollständige Backup nutzen.

##  Wichtige Fragen, die es zu beantworten gilt
Wichtige Fragen in Bezug auf Backups sind:
1. Zugriffs-Schutz: Wer hat Zugriff zu Backups?
2. Rechenzentrums-Ausfall: Was geschieht, wenn das gesamt Rechenzentrum ausfällt?
3. Datenschutz-Anforderungen: Wie sensibel sind die Backup Daten?
4. Wiederherstellung: Wiederherstellung beschreibt den Kontext der Rettung von Anwendungen, ihrer Daten und Konfigurationen im Katastrophenfall.  Damit stellt sich die Frage: Was ist die Dauer für die Wiederstellung?

##  Besonderheiten beim Backup von Logfiles 
###  Weiterführende Analyse Möglichkeiten mit Log Backups
Das Backup ermöglicht etwas speziellere Analytik. Die Logfiles können zum Beispiel auf nicht autorisierte Änderungen analysiert werden und so einen weiteren Indikator für Angriffe liefern.

###  Log-Daten Behandlung mit ubuntu12.04
|Aktueller Name	|Häufigkeit	|Komprimierung	|Generationen	|Unkomprimierter Name	|
|auth.log		|2d			|1+				|6				|auth.log.0				|
|syslog			|1d			|1+				|6				|syslog.0				|
|apache*		|1w			|1+				|52				|access.log.1			|
|catalina.out	|1w			|0+				|52				|--						|

##  Besonderheiten bei HostEurope
Das Beispiel Unternehmen hat seine Server  bei HostEurope gehostet. Nach der HostEurope Produktbeschreibung sind für das Beispiel Unternehmen die folgenden Backup Optionen verfügbar:
Snapshot: verwahrt den ganzen Server (Anwendung, Konfiguration, Daten) – die Wiederherstellung dauert ca. 2-5 Stunden. Die Snapshots werden drei Monate lang aufbewahrt.
Permanenter Snapshot: Vergleichbar mit Snapshots, nur mit unbegrenzter Aufbewahrungszeit.
File-System Backup: auf Basis eines täglichen Backups, wird für die letzten 14 Tage aufbewahrt.