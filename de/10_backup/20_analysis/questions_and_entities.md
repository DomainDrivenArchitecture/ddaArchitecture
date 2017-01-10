# Fragen, die für ein Backup wichtig sind
## Welche Daten sollen gesichert werden?
Die folgende Begriffe sind für die Frage "was wollen wir sichern" wichtig:
1. Anwendungs-Code: Code für individuelle Anwendungs-Installationen.
2. Anwendungsdaten: Daten der installierten und genutzten Anwendungen.
3. Konfiguration: Konfiguration der Komponenten oder Anwendungen.
4. Logdaten: Logfiles für genutzte Anwendungen.
5. Sicherheits-Logdaten: spezielle Sicherheits-Logfiles (für gesichterte Systeme).

## Nutzen wir Deduplizierung?
Um Speicherplatz, Übertragungs-kapazität und Backupzeit einzusparen, arbeiten manche Lösungen mit Teilbackups. 
1. Vollständiges Backup: Alle Daten werden in einer Backup-Einheit gesichert. Zur Widerherstellung ist nur diese eine Backup Einheit nötig.
2. Inkrementelles Backup: Nur geänderte Daten werden gesichert. Zur Widerherstellung sind mehrere aufeinanderfolgende Backupeinheiten nötig.

## Welche Daten-Sicherheit benötigen wir?
Wichtige Fragen in Bezug auf Backups sind:
1. Zugriffs-Schutz: Wer hat Zugriff zu Backups?
2. Datenschutz-Anforderungen: Wie sensibel sind die Backup-Daten?

## Was ist für die Widerherstellung wichtig?
1. Rechenzentrums-Ausfall: Was geschieht, wenn das gesamte Rechenzentrum ausfällt, soll eine Widerherstellung möglich sein?
2. Wiederherstellungs Zeit und Vorbedingungen: Wiederherstellung beschreibt den Kontext der Rettung von Anwendungen, ihrer Daten und Konfigurationen im Katastrophenfall.