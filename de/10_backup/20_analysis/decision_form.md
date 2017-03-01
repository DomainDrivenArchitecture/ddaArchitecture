# Backup Entscheidungen
## Generelle Entscheidungskriterien
Wenn wir über Backup nachdenken, dann können die folgenden Elemente relevant sein:
 * Systemkonfiguration: Konfiguration und Installationszustand des zugrundeliegenden Systems.
 * Applikationskonfiguration: Die einstellungen der eigentlichen Anwendung
 * Applikations-Binaries: Die ausführbaren Dateien einer Anwendung.
 * Anwendungsdaten: Die Daten, die bei der Nutzung der Anwendung entstehen.
 * Logdaten: Logmeldungen, die wichtige Ereignisse protokollieren.

## Entscheidungskriterien je Anwendung
Neben den eigentlichen Backup-Inhalten (für deren Backup generelle Richlinien gelten können) muss natürlich auch die einzelne Anwendung betrachtet werden:

|ID									|Messgröße|
|--									|--|
|Anwendungsname						||
|Aktuelle Datengröße der Anwendung	||
|Erwartetes Datenwachstum der Anwendung für das bevorstehende Jahr||
|Logdaten Wachstum / Jahr			||
|Anwendungsdaten-Backup auf dem „Source“- System||
|Generationen im Tagesintervall		||
|Generationen im Wochenintervall	||
|Generationen im Monatsintervall	||
|Anwendungsdaten-Backup auf dem „Sink“-System||
|Generationen im Tagesintervall		||
|Generationen im Wochenintervall	||
|Generationen im Monatsintervall	||
|Anforderungen der Anwendung		||
|Wichtigkeit / Verfügbarkeit der Anwendungsdaten||
|Vertraulichkeit der Anwendungsdaten|| 
|Vertraulichkeit der Logdaten		|| 
|Wiederherstellungszeit im Katastrophenfall|||


# Entscheidungs-Beispiel für das "Beispiel Unternehmen"
## Generell
Wir machen für Anwendungsdaten und Logdaten ein Backup.
Code und Konfigurationen benötigen kein Backup, da der Code im Versions Management System gespeichert ist.
* **Systemkonfiguration:** Wird vollständig durch ConfigManagement erstellt und ist daher immer reproduzierbar. - Kein Backup Bedarf.
* **Applikationskonfiguration:** Wird vollständig durch ConfigManagement erstellt und ist daher immer reproduzierbar. - Kein Backup Bedarf.
* **Applikations-Binaries:** Binaries werden für das ConfigManagement auf einem speziellen Artefakt-Server abgelegt. - Kein zusätzlicher Backup Bedarf, allgemeine Aufbewahrungszeit: 1 Jahr.
* **Anwendungsdaten:** Werden gemäß Kriterien-Tabelle gesichert - Backup Bedarf.
* **Logdaten:** Logdaten werden zwar teilweise in Echtzeit Aggregiert und gesammelt (Logstash, Ossec), für eine vertiefte Analyse sollen Logdaten allerdings zusätzlich gesichert werden. Logdaten werden also gemäß Kriterien-Tabelle gesichert - Backup Bedarf, allgemeine Aufbewahrungszeit: 1 Jahr.

## Je Anwendung
Für die Festlegung der Anwendungs-Individuellen Bedarfe haben wir die o.g. Tabelle verwendet. Für die Verfügbarkeit nutzen wir dei folgende Definition:

**Definition Verfügbarkeit**
* Hoch: Hoch wichtige Daten werden in einem anderen Rechenzentrum aufbewahrt.
* Normal: Normal wichtige Daten werden auf einem anderen Server aufbewahrt.
* Niedrig: Weniger wichtige Daten werden nur auf dem gleichen Server und im Backup Store des Hosting Providers aufbewahrt.

