# Umsetzung unter Verwendung des dda-backup-crate
## [dda-backup-crate](https://github.com/DomainDrivenArchitecture/dda-backup-crate)
* Das Arbeitspaket nutzt Clojure/Pallet zur Konfiguration.
* Für verschiedene Applikationen können spezifische Lösung gehandhabt werden, beispielsweise für Owncloud oder JIRA.
* Der dda-backup-crate erlaubt Instanziierbarkeit.
* Es werden die Kommandozeilen-Befehle für die Installation eines applikations- und instanzspezifischen Backup-Systems logisch gebündelt und im Pallet-Kontext ausgeführt.
* Welche Befehle für einen Backup nötig sind, ist den Dokumentationen der entsprechenden Applikationen zu entnehmen.

## Methode install-backup-app-instance
* Die Methode **org.domaindrivenarchitecture.pallet.crate.backup/install-backup-app-instance** wird bei der Installation des Backups aufgerufen.
* Sie erhält folgende Eingabe-Parameter:

| Parameter       | Bedeutung     |
| --------------- |-------------|
| app-name        | Der Applikationssname (z.B. JIRA) |
| instance-name        | Der Instanzname     |
| backup-lines   | Kommandozeilen-Befehle zur Einrichtung des Backup-Prozesses  |
| source-transport-lines | Kommandozeilen-Befehle zur Einrichtung des Transport-Prozesses |
| restore-lines | Kommandozeilen-Befehle zur Einrichtung des Restore-Prozesses |
 
* Pro Applikation werden die drei Kommandozeilen-Befehls-Listen definiert.
* Es ist sinnvoll, diese Definitionen in einen eigenen Namensraum (Namespace) zu packen.
* Es ist sinnvoll, diese Definitionen parametrisierbar zu definieren, also sie z.B. mit einem Parameter für den Instanznamen zu versehen.  



