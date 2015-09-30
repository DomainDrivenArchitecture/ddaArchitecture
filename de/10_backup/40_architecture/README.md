# Architecture
## Kontext
Die beschreibenen Backup-/Restore-Prozesse beleuchten nur den Teil der 

## Entscheidungen
### Datentransport nach dem Pull-Verfahren.
Backups werden ausschließlich von den Sink-Systemen im Pull-Verfahren bezogen. Diese Entscheidung hat die folgenden Gründe:
  * Sicherheit: Sollte ein einzelner Applikationsserver korrumpiert werden, so sind die Backupdaten sicher. Der Angreifer findet für nachfolgende Backupsysteme keine Credentials vor.
  * Netzwerk-Zugriff: Zur Absicherung gegen die unterschiedlichen Risiken müssen Backups "außerhalb" gespeichert werden. "Außerhalb" bedeutet auch außerhalb von Netzwerkzonen. Um die zentraleren Backup-Speicher nicht exponieren zu müssen, werden Datentransporte daher stets vom zentraleren System angestoßen.    

### Todo
* Autorisierung
* Prüfung
* Benachrichtigung