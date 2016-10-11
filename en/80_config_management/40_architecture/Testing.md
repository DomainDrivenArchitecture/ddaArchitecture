#Testing

Alle Actions werden mit Pallet realisiert und in einer eigenen Phase (test) ausgeführt.

1) Zu prüfende / überwachende Resourcen können festgelegt werden.

* Dabei wird eine eindeutige Kennung der Resource angegeben. 
  Um Mehrfachverwendung zu vermeiden Vorschlag: crate_resource, z.B. dda-servertest-crate_apt-packagelist
* State wird angelegt unter /home/pallet/state/$timestamp/

  (serverstate/define-check-file some-handle "...")
  Idee: File wird kopiert in /home/pallet/state-$timestamp/, Fehler falls nicht vorhanden

  (serverstate/define-check-script some-handle "...")
  Idee: Script wird ausgeführt (errorcode <> 0 = fehler) und ausgabe nach /home/pallet/state-$timestamp/... zum untersuchen

  (serverstate/define-check-filetree some-handle "path")
  Idee: Mit "find path" wird Dateibaum erzeugt


2) Inhalte können verifiziert werden

* Checkscripte sollen vernünftige (lesbare) outputs erzeugen, dass diese im Nachgang gespeichert/analysiert werden können.
* Checks sollen auf dem Server unter /home/pallet/state-$timestamp/checks abgelegt sein

z.B.
  (serverstate/check-content some-handle content)
  überprüft ob content exakt gleich

  (serverstate/check-contains(-not) some-handle content)
  überprüft ob ein ausschnitt (nicht) vorhanden ist

  (serverstate/check-regex some-handle content)
  überprüft den regexp auf den inhalt

Helfer wie
  (serverstate/check-file-exists some-path)
  (serverstate/check-installed some-pkg)


3) Erweiterung: Diffs zwischen den States anzeigen, Tests mit Diffs
z.B.
  (serverstate/check-nodiffs some-handle)


4) Phase clear-state löscht alte states




-------------

Vordefinierte Tests im server-test-crate:


* apt-package-list		
apt list --installed

* apt-repository-list
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*

* os-version
cat /proc/version
cat /etc/os-release

* disk-status	
df
Skript konfigurierbar --> Thresholds können angegeben werden

* network
ifconfig

* ports
netstat ...