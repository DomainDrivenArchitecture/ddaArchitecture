# Analysis

##Why do we need Config Management?
* repeatability - server-setup should be repeatable for controlled fixing of issues.
* automate&hide - boring details like file-mode or owner should be automated
* Handle large number of servers
* React fast for demand for new servers
* Standardize components setup

##What's difficult at Config Management?
* There are many cross cutting dimensions for modules (tenant, security, functionality, backup, identity on various levels, different environments per appstack ...)
* There are different deployed versions of configuration on servers
* blind shoot server configuration is dangerous
* config management should be well tested
* Target systems differ on wide range (e.g. operating system, server, desktop, device type like smartphone)
* Pull / Push is both needed.
  * Push is important for security reason (server-credentials may not reside on every server in net)
  * Pull is important for social & technical reason (not accessible nets / developers don't like uncontrolled updates)
  
##Insigths
* Configuration is an central entity in Config Management
* Following module types can be distinguished:
  * CM core modules - things like CM transport & execution, target fact recognition
  * CM middleware modules - like httpd, backup or hardening
  * CM App-Stacks - like owncloud consisting of httpd, database, app, backup, hardening, monitoring and individual configuration.
  
  
