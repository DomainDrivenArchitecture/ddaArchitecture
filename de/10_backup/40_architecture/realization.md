# Umsetzung 

Im Folgenden werden reale Umsetzungen beschrieben, z.B. anwendbar auf die Applikationen
* JIRA 
* Ownlcoud
* Liferay 
* Sugar CRM

## Modulkonfigurationen
 
* org.domaindrivenarchitecture.pallet.crate enthält die Konfiguration der Module (facilities).  
 

## Module
*  Die Namen der Module sind z.B. dda-liferay oder dda-jira.

* Beispiel:
* (def facility :dda-jira)      ;Facility
* (def app-name (name facility))    ;AppName = Name des Moduls

## Instanzen
* Einzelne Module können mehrfach instanziierbar sein.
* D.h. die Modulkonfigurationen müssen verschiedene Instanzen unterscheiden können.
* Das bedeutet, dass auch der Backup eine Unterscheidung zwischen den Instanzen von Modulen vornehmen können muss.
* Instanzen sind unterscheidbar anhand ihrer Id. Aus Gründen der Lesbarkeit, bekommen unterschiedliche Instanzen unterschiedliche semantische Namen:
* semantic-name
* Auch wenn ein Modul nur eine Instanz hat, so hat es einen semantic-name


### Skripte im Filesystem

* Es werden grob zwei Arten von Skripten genutzt
* cronjob-Skripte
* Modul- und instanzspezifische Backup-/Restore-Skripte

* cronjob-Skripte liegen in /etc/cron.daily/
* außerdem finden sich hier Links auf Backup- und Transportskripte

* Backup- und Restore-Skripte liegen in /usr/lib/dda-[app-name]/

#### Manueller Restore

* ein Restore-Skript benötigt den gemeinsamen Präfix der Restore-Files als Parameter
  * Beispielaufruf für folgenden Restore (gemeinsamer Präfix: "dda-myBackup\_"):
    * dda-myBackup\_file\_2015-08-09_05-14-08.tgz
    * dda-myBackup\_mysql\_2015-08-09_05-14-08.sql
  *  /usr/lib/dda-[app-name]/myBackup\_restore.sh dda-myBackup\_
* das Restore-Skript nutzt den Stand mit dem neusten Zeitstempel
* nach dem Restore ist der Server neuzustarten
 