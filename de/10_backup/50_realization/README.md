# Umsetzung unter Verwendung des dda-backup-crate

TODO review mje 27.6.2015: 
Diese Beschreibung bitte nach README_de.md in den Backup-Crate packen.
Vorlage einer guten Beschreibung ist der httpd crate

## [dda-backup-crate](https://github.com/DomainDrivenArchitecture/dda-backup-crate)
* TODO review mje 27.6.2015: - im Kontext BackupCrate ist diese Info nicht mehr nötig:Das Arbeitspaket nutzt Clojure/Pallet zur Konfiguration.
* TODO review mje 27.6.2015: welche Info bekommt der Leser hier? Für verschiedene Applikationen können spezifische Lösung gehandhabt werden, beispielsweise für Owncloud oder JIRA.
* Der dda-backup-crate erlaubt Instanziierbarkeit.
* Es werden die Kommandozeilen-Befehle für die Installation eines applikations- und instanzspezifischen Backup-Systems logisch gebündelt und im Pallet-Kontext ausgeführt.
* Welche Befehle für einen Backup nötig sind, ist den Dokumentationen der entsprechenden Applikationen zu entnehmen.

TODO review mje 27.6.2015:  das dings macht:
User anlegen, Dir-Struktur anlegen, Scripte zum Backup ablegen, chronjob eintragen. Dazu jeweils 1-2 Sätze.

## compatability

This crate is working with:
 * pallet 0.8
 * ubuntu 14.04
 * TODO review mje 27.6.2015: Aufführen, welche apt-get pakete wir hier verwenden.
 
## Features
 * kann files (tar od. als directory diff), datenbanken (mysql)
 * sichern, 
 * generationen verwalten
 * wieder herstellen

## Methode install-backup-app-instance

TODO review mje 27.6.2015: Das sind zum einen Fehler (wir haben hier keinen Instanzname - auch wenn das vielleicht die bessere Bezeichnung wäre ...) drin, zum anderen weiß der Benutzer nicht, wie dat janze eingesetzt werden kann. Dazu musst du eigentlich nur Beispiele aus unserem code nehmen ...

* Die Methode **org.domaindrivenarchitecture.pallet.crate.backup/install-backup-app-instance** wird bei der Installation des Backups aufgerufen.
* Sie erhält folgende Eingabe-Parameter:

| Parameter       | Bedeutung     |
| --------------- |-------------|
| app-name        | Der Applikationssname (z.B. JIRA) |
| instance-name   | Der Instanzname     |
| backup-lines   | Kommandozeilen-Befehle zur Einrichtung des Backup-Prozesses  |
| source-transport-lines | Kommandozeilen-Befehle zur Einrichtung des Transport-Prozesses |
| restore-lines | Kommandozeilen-Befehle zur Einrichtung des Restore-Prozesses |
 
* Pro Applikation werden die drei Kommandozeilen-Befehls-Listen definiert.
* Es ist sinnvoll, diese Definitionen in einen eigenen Namensraum (Namespace) zu packen.
* Es ist sinnvoll, diese Definitionen parametrisierbar zu definieren, also sie z.B. mit einem Parameter für den Instanznamen zu versehen.  


 
## Usage Examples - Bsp. aus httpd crate

Required dependencies

    (require '[pallet.actions :as actions])
    (require '[pallet.api :refer [group-spec server-spec node-spec plan-fn]])
    (require '[pallet.crate.automated-admin-user :refer [automated-admin-user]])
    (require '[httpd.crate.apache2 :as apache2])
    (require '[httpd.crate.cmds :as cmds])

    (use 'pallet.repl)

Configure a base server that allows us to connect via ssh using
private key and also automatically runs apt-get update

    (def base-server
      (server-spec
        :phases
        {:bootstrap (plan-fn 
            ;; setup private key ssh
            (automated-admin-user)
            ;; update packages
            (actions/package-manager :update))}))

Create the pallet service and node-spec

    (def s (pallet.configure/compute-service :vmfest))
    (def default-node-spec
      (node-spec
        :image {:image-id :ubuntu-14.04}
        :hardware {:min-cores 1}))
        
Define a group-spec that extends `apache2/server-spec`. The
`apache2/server-spec` will install apache2 package during configure
phase and adds a `:restart` :phase for conveniently restarting apache.
If/when someone has time, we want to eventually provide a lot more
options so that the `apache2/server-spec` can control much more.

    (def apache2
      (group-spec "apache2"
        :extends [base-server 
             (apache2/server-spec {})]
        :node-spec default-node-spec))

Use converge to bring up http server and install apache2

    (session-summary
      (pallet.api/converge {apache2 1} :compute s))

Enable a couple mods and restart

    (session-summary
      (pallet.api/converge {apache2 1}
          :compute s
          :phase (plan-fn (cmds/a2enmod "rewrite")
                          (cmds/a2enmod "headers")
                          (cmds/apache2ctl "restart"))))

Setup mod-gnutls

    (require '[httpd.crate.mod-gnutls :as gnutls])
    (session-summary
      (pallet.api/converge {apache2 1}
          :compute s
          :phase (plan-fn (gnutls/install-mod-gnutls)
                          (gnutls/configure-gnutls-credentials
                              :domain-name "your-domain.com"
                              :domain-cert "your cert file"
                              :domain-key "your key file"
                              :ca-cert "your cert file"))))

Setup mod-proxy-http

    (require '[httpd.crate.mod-proxy-http :as proxy])
    (session-summary
      (pallet.api/converge {apache2 1}
          :compute s
          :phase (plan-fn (proxy/install-mod-proxy-http))))

Configure limits

    (require '[httpd.crate.config :as conf])
    (session-summary
      (pallet.api/converge {apache2 1}
          :compute s
          :phase (plan-fn (apache2/configure-file-and-enable
                           "limits.conf" conf/limits))))

Configure security

    (session-summary
        (pallet.api/converge {apache2 1}
            :compute s
            :phase (plan-fn (apache2/configure-file-and-enable
                             "security.conf" conf/security))))

Configure ports

    (session-summary
        (pallet.api/converge {apache2 1}
            :compute s
            :phase (plan-fn (apache2/configure-file-and-enable
                             "ports.conf" conf/ports))))
                             
Setup mod_jk

    (require '[httpd.crate.mod-jk :as jk])
    (session-summary
      (pallet.api/converge {apache2 1}
          :compute s
          :phase (plan-fn (gnutls/install-mod-jk)
                          (gnutls/configure-jk-worker))))


Setup vhosts. Here's an example of a fairly complicted vhost: 

    (require '[httpd.crate.vhost :as vhost])
    (require '[httpd.crate.basic-auth :as auth])

    (def vhost-content
      (into 
      []
        (concat
          (vhost/vhost-head :listening-port "443"
                            :domain-name "domain-name" 
                            :server-admin-email "server-admin-email")
          (proxy/vhost-proxy :target-port "app-port") 
          (vhost/vhost-location
             :location-options
             (auth/vhost-basic-auth-options :domain-name "domain-name"))
          (vhost/vhost-log 
           :error-name "error.log"
           :log-name "ssl-access.log"
           :log-format "combined")
          (gnutls/vhost-gnutls "domain-name")
          vhost/vhost-tail)))

    (session-summary
        (pallet.api/converge {apache2 1}
            :compute s
            :phase (plan-fn (apache2/configure-and-enable-vhost
                             "000-default" vhost-content))))

There are a few other fn's inside `apache2.crate.vhost` such as
`vhost/vhost-conf-default-redirect-to-https-only` that are convenient
for creating content to pass to `apache2/configure-and-enable-vhost`

## License

Copyright © 2015, Michael Jerger, Tobias Scherer

Distributed under the Apache 2.0 License.
