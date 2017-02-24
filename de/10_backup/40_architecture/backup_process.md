# Schritte des Backup Prozesses

![the backup process][backup process]

[backup process]: https://raw.githubusercontent.com/DomainDrivenArchitecture/ddaArchitecture/ali/images/10_backup/backup_phases.png "the backup process"

## Backup Quelle
### Backup durchführen (1)
Im Backup Schritt ist ein Cronjob auf dem „Source“-System dafür zuständig,
1. den laufenden Applikationsserver zu stoppen (1.a).
2. alle Anwendungsdaten (1.b) und Logdaten (1.d) zu sammeln.
3. den Applikationsserver wieder zu starten (1.c).
4. die gesammelten Daten an den  “Transport Handover Point” zu übergeben.
5. den “früherer Transport ist fehlgeschlagen”-Fall zu behandeln und z.B. eine Fehler-Mail zu verschicken.

## Backup Daten Transport (2)
### Den Transport durchführen - im Push-Mode (2.a)
Im Transport-Schritt ist ein Cronjob auf dem „Source“-System dafür zuständig, 
1. den Transport durchzuführen(2.a): Der dataBackupSource User ist für seinen Store auf dem „Sink“-System autorisiert.
2. (optional) Überprüfung auf Fehlerfreiheit: Wird z.B. per Hashvergleich sichergestellt.
3. „Sink“-Generationen zu behandeln: Löscht die ältesten Backups, welche die gewählte Anzahl der aufzubewahrenden Backup-Generationen überschreitet.
4. zum „Source-Store“ zu verschieben (2.c): Verschiebt das erhaltene Backup zum „Source-Store“.
5. „Source“-Generationen zu behandeln: Löscht Backups, gemäß der gewählten Source-System-Generationen.

### Alternativ: Den Transport durchführen - im Pull-Mode (2.a)
Im Transport-Schritt ist ein Cronjob auf dem „Sink“-System dafür zuständig, 
1. den Transport durchzuführen(2.a): Das „Sink“-System ist für den dataBackupSource User berechtigt.
2. (optional) Überprüfung auf Fehlerfreiheit: Wird z.B. per Hashvergleich sichergestellt.
3. zum „Sink-Store“ (2.b)zu verschieben: Verschiebt das erhaltene Backup zum „Sink-Store“.
4. „Sink“-Generationen zu behandeln: Löscht die ältesten Backups, welche die gewählte Anzahl der aufzubewahrenden Backup-Generationen überschreitet.
5. zum „Source-Store“ zu verschieben (2.c): Verschiebt das erhaltene Backup zum „Source-Store“.
6. „Source“-Generationen zu behandeln: Löscht Backups, gemäß der gewählten Source-System-Generationen.

## Backup Log Transport (3)
Im Transportschritt ist ein Cronjob des „Sink“-Systems dafür zuständig,
1. den Transport durchzuführen(3.a): mittels ssh und rsync. Das „Sink“-System ist per ssh-Zertifikat für den logBackupSource user berechtigt .
2. (optional) auf Fehlerfreiheit zu überprüfen: Wird durch einen Hashvergleich sichergestellt.
3. zum „Sink-Store“ (3.b) zu verschieben: Verschiebt das erhaltene Backup zum „Sink-Store“.
4. „Sink“-Generationen zu behandeln: Löscht die ältesten Backups, welche die gewählte Anzahl der aufzubewahrenden Backup-Generationen überschreitet.