# Analysis

##Why do we need Config Management?
* repeatability - server-setup should be repeatable for controlled fixing of issues.
* automate&hide - boring details like file-mode or file-owner should be automated away.
* Handle large number of servers
* React fast on demand for new servers
* Standardize components setup - so all installed system will benefit from new insights. 

##What's difficult at Config Management?
* There are many cross cutting dimensions for modules (tenant, security, functionality, backup, users identity on various levels, different environments for one application stack ...)
* There are different deployed versions of configuration on servers
* Blind shoot server configuration is dangerous
* Configurations in config management should be well tested
* Target systems differ on wide range (e.g. operating system, server, desktop, device type like smartphone)
* Pull / Push both methods are needed.
  * Push is important for security reason (server-credentials may not reside on every server node in net)
  * Pull is important for social & technical reason (some nets may be not accessible from outside / or developers don't like uncontrolled updates from outside)
  
##Insigths
* Distinguishing the following module types might be useful:
  * CM core modules - things like CM transport & execution, target fact recognition
  * CM middleware modules - like httpd, backup or hardening
  * CM App-Stacks - like owncloud consisting of httpd, database, app, backup, hardening, monitoring and individual configuration.
  * Configuration is an central concept in Config Management. Therefore Configuration would be a CM core module.
  
  
