#Config-management-Branch
## Architecture

### Modularization
#### Modules and Building Blocks
* adjust diagram , e.g. config crate is deprecated and dda-pallet is missing
* adjust text accordingly
*  Also crosscutting aspects like backup, monitoring, -> are we using monitoring really?

#### Core Modules
##### dda-configuration
* adjust to deprecated dda-config-crate
#### ddaInit
* do we really use docker?
#### ddaBase
* With our servertest-crate we adjusted our state management slightly, we need to adjust accordingly
* base crate doesnt exist anymore, do we mean basic crate?

#### Phases
* init -> do we still use an explicit init-phase?
* configure: on a regular base -> basis
* test, maybe link to the testing chapter?

#### State Management
* adjust to servertest-crate accordingly

#### Credentials Security Solution
#####  Factors for encryption / decryption
* So beound the pallet -> beyond

#### Testing
TODO:
Add context for resources & tests
introduce xBox-Tests
introduce test Scopes
introduce cost @analysis

* i think we want to include a picture here but the link is broken
* TODO: Move this information to relization part

## Requirements
### Requirements Httpd
* https://dda.gitbooks.io/domaindrivenarchitecture/content/v/configmanagement/en/80_config_management/30_requirements/index.html
* DevOps should be able to install System Components by configuring as view configuration as possible. -> "view" -> "few"
  * Eventuell ändern: "DevOps should be able to install System Components by keeping configuration to a minimum required."
* "Multi Tenant configuration can be handled separated per tenant" -> "Multi Tenant configuration can be handled seperatly per tenant"
* "The following dimensions are used for resolfing overwrite:" -> resolving
  * Was genau möchtest du hier mit "dimensions" ausdrücken?
* req0036 Document Root is configurable -> ist das noch so? ich hab nichts der gleichen gefunden
* req0039 Module supports multi-tier maintainance page -> multi-tier maintenance page
* zu "Load Test" -> * req0042 Logging fits the load test : Was genau ist damit gemeint?
                    * req0043 Sysstat fits the load test : Ich glaube wir installieren sysstat momentan noch nicht das war ja die
                      Idee hinter dem monitoring crate

###  Requirements Liferay
* Release Management (phase :prepare-rollout) wir haben ein cold und hot deploy ist das mit hot und full gemeint und abgedeckt?

### Managed Desktop Foundations
* req0070 VM Integration "Shared Folders" brauchen zusätzliche Konfiguration mit Virtualbox unser CMS unterstützt das nicht direkt,
  gilt für die restlichen genauso
* req0076 DesktopWiki hier hat sich die Solution geändert da wir nicht mehr anacron verwenden
* zu *Convienience* Fakturama, zim, owncloud haben wir noch, bewusst weg gelassen?

### Managed IDE
#### Operating System
* ist mittlerweile Xubuntu 14.04.5 LTS (Trusty Tahr)
#### Communication
* Was ist Madeye?
#### Office Integration
* xubuntu version anpassen
* Verwenden wir noch KMail oder Thunderbird?
#### Credentials Security
* req0226 - req0233 404 Fehler




## Realization
### Module WebServer
* we do not configure our webserver and vhost like this anymore, instead we use maps as configuration
	


