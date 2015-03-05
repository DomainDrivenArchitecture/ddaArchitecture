# Varianten von Backup Daten
1. Anwendungs-Code: Code für individuelle Anwendungs-Installationen.
2. Anwendungs-Daten: Daten der installierten und genutzten Anwendungen.
3. Konfiguration: Konfiguration der Komponenten oder Anwendungen.
4. Log Daten: Logfiles für genutzte Anwendungen.
5. Sicherheits-Log Daten: Für gesicherte Systeme gibt es spezielle Sicherheits-Logfiles.

# Backup Daten Deduplizierung
Auch wenn es viele Zwischenvarianten gibt, werden wir hier nur nach den zwei Hauptvarianten unterscheiden:
1. Vollständiges Backup
2. Inkrementelles Backup
Aufgrund der kleinen Backup-Größe bei unserem Beispiel Unternehmen, werden wir nur das vollständige Backup nutzen.

# Wichtige Fragen, die es zu beantworten gilt
Wichtige Fragen in Bezug auf Backups sind:
1. Zugriffs-Schutz: Wer hat Zugriff zu Backups?
2. Rechenzentrums-Ausfall: Was geschieht, wenn das gesamt Rechenzentrum ausfällt?
3. Datenschutz-Anforderungen: Wie sensibel sind die Backup Daten?
4. Wiederherstellung: Wiederherstellung beschreibt den Kontext der Rettung von Anwendungen, ihrer Daten und Konfigurationen im Katastrophenfall.  Damit stellt sich die Frage: Was ist die Dauer für die Wiederstellung?