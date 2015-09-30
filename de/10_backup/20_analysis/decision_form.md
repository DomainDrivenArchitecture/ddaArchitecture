# Backup Entscheidungen
## Generelle Entscheidungskriterien

Allgemeine Entscheidungen
### Datentypen für das Backup
Wir machen für Anwendungsdaten und Logdaten ein Backup.
Code und Konfigurationen benötigen kein Backup, da der Code im Versions Management System gespeichert ist.
 * Anwendungsdaten
 * Logdaten werden täglich synchronisiert. Aufbewahrungsdauer ist z.B.: 1 Jahr
   * Begründung:
 * Sicherheits-Logdaten: Sicherheits-Logs benötigen kein Backup, da sie in Echtzeit synchronisiert werden. Aufbewahrungsdauer ist z.B.: 1 Jahr

Allgemeine Entscheidungen
### Datentypen für das Backup
Wir machen für Anwendungsdaten und Logdaten ein Backup.
Code und Konfigurationen benötigen kein Backup, da der Code im Versions Management System gespeichert ist.
 * Anwendungsdaten
 * Logdaten werden täglich synchronisiert. Aufbewahrungsdauer ist z.B.: 1 Jahr
   * Begründung:
 * Sicherheits-Logdaten: Sicherheits-Logs benötigen kein Backup, da sie in Echtzeit synchronisiert werden. Aufbewahrungsdauer ist z.B.: 1 Jahr


## Entscheidungskriterien je Anwendung
### Definition Verfügbarkeit
* Hoch: Hoch wichtige Daten werden in einem anderen Rechenzentrum aufbewahrt.
* Normal: Normal wichtige Daten werden auf einem anderen Server aufbewahrt.
* Niedrig: Weniger wichtige Daten werden nur auf dem gleichen Server und im Backup Store des Hosting Providers aufbewahrt.



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
|Wiederherstellungszeit im Katastrophenfall||

Entscheidungsbeispiel in der 