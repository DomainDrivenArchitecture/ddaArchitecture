# Implementation

Realizations are described below, e.g. Applicable to the applications
* JIRA
* Ownlcoud
* Liferay
* Sugar CRM

## Module Configurations
 
* Org.domaindrivenarchitecture.pallet.crate contains the configuration of the modules (facilities).
 

## Modules
* The names of the modules are e.g. Dda-liferay or dda-jira.

* Example:
* (Def facility: dda-jira); Facility
* (Def app-name (name facility)); AppName = name of the module

## Instances
* Individual modules can be instanced several times.
* For example the module configurations must be able to distinguish between different entities.
* This means that the backup must also be able to distinguish between instances of modules.
* Instances are distinguishable by their id. For reasons of readability, different instances get different semantic names:
* Semantic-name
* Even if a module has only one instance, it has a semantic-name


### Scripts in the filesystem

* There are used two types of scripts roughly
* Cronjob scripts
* Module- and instance-specific backup / restore scripts

* Cronjob scripts are located in /etc/cron.daily/
* Also links to backup and transport scripts can be found here

* Backup and restore scripts are located in /usr/lib/dda-[app-name]/

#### Manual Restore

* A restore script needs the common prefix of the restore files as parameters
  * Example call for the following restore (common prefix: "dda-myBackup \ _"):
    * Dda-myBackup\_file\_2015-08-09_05-14-08.tgz
    * Dda-myBackup\_mysql\_2015-08-09_05-14-08.sql
  * /usr/lib/dda-[app-name]/myBackup\_restore.sh dda-myBackup\_
* The Restore script uses the state with the latest time stamp
* Restart the server after restoring