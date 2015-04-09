# Umsetzung 

Im Folgenden werden reale Umsetzungen beschrieben. Es zeigt Umsetzungen für folgende Server-Applikationen:
* JIRA (kleines Beispiel)
* Liferay (ausführlicheres Beispiel)

## Grundsätzliches
* Grundsätzlich soll der Backup von unterschiedlichsten Modulen funktionieren.
* Auch der Backup von verschiedenen Instanzen des gleichen Moduls sollen problemlos ablaufen.
 
## Module
* org.domaindrivenarchitecture.pallet.crate enthält die Konfiguration der Module (facilities). 
* Die Namen der Module sind dda-liferay oder dda-jira.
* Auf dieser Ebene werden die  Installation und die Konfigurationen beschrieben.
* Die install-Phase übernimmt also (u.A.) die Einrichtung des Backupsystem...
* ... während die configure-Phase die Konfiguration übernimmt.

## Instanzen
* Einzelne Module können mehrfach instanziierbar sein.
* D.h. die Modulkonfigurationen müssen verschiedene Instanzen unterscheiden können.
* Das bedeutet, dass auch der Backup eine Unterscheidung zwischen Modulen und Instanzen vornehmen können muss.

