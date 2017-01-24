#Backup-Branch

Architecture:
* backup process
* https://dda.gitbooks.io/domaindrivenarchitecture/content/v/backup/en/10_backup/40_architecture/backup_process.html
* Bild: HostEuropre abstrahieren und generisch an einen Provider anpassen
* Use HostEuropre Backup (4) -> generisch zu Provider ändern

* restore process
* https://dda.gitbooks.io/domaindrivenarchitecture/content/v/backup/en/10_backup/40_architecture/restore_process.html
* Restore Data Transport (1) -> generisch auf Provider ändern
* 2) Restore Data Transport (1) -> versteh ich nicht ganz... (hat das was mit den ssh-keys zu tun?)
*

* Source
* https://dda.gitbooks.io/domaindrivenarchitecture/content/v/backup/en/10_backup/40_architecture/source.html
* Local Backup Store Folder -> da stimmt was mit der Formatierung nicht und ist damit schwer zu lesen

* Sink
* https://dda.gitbooks.io/domaindrivenarchitecture/content/v/backup/en/10_backup/40_architecture/sink.html

Realization:
* dda-backup-crate
* https://dda.gitbooks.io/domaindrivenarchitecture/content/v/backup/en/10_backup/50_realization/index.html
* -> "Specific adapters has to be defined." sollte heißen:
   "Specific adapters have to be defined."
* Hier hat sich/wird sich noch viel ändern (duplicity). Eventuell erneut betrachten wenn sicher ist wie sich der backup-crate
  verändert


* Requirements
* https://dda.gitbooks.io/domaindrivenarchitecture/content/v/backup/en/10_backup/30_requirements/index.html
* Requirements Backupdauer: Das Backup ist auf eine maximale Laufzeit von 2h begrenzt. -> Warum
