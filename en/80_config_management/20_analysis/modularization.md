# Modularization
## How can configuration be modularized?
## Which dimensions are important for cutting off the building blocks?
There are many relevant Dimensions for cutting modules
* tenants, 
* different system environments like dev, test, staging, integration or production 
* cross cutting functions like security, backup, users identity on various levels
* operating systems
* cloud / hosting providers
* cloud provider types
* container types

TBD
The ExecutionContext encapsulates the state recognized for application of config management:
* pointInTime - the current world time
* organisationUnit - the organizational execution context. May be tenant or finer grained organizational units. 
* targetSystem - pallet default representation of target system facts like ip, os-type and so on.
* targetInstallationState - additional dda representation of target system's installation state.  
* targetEnvType - additional dda represantation of target environment type like dev, test, integration or production.  

## Can it-ops services be abstracted and integrated?

## What does dda-platform mean?
All dimensions dda can be hide transparently away from crate users we will call dda-platform. Dimensions considered to be hidden are:
* Operating system
* cloud / hosting provider

## How can we apply same modules on different platforms?
## How can / should Configuration Management support many instances on single server?
## What elements are important for handling versions?
There will always be the situation of different versions of deployed software. Distinguishing between debit and actual. "Configuration" denominates the pursued debit, the actual state of server nodes we will name "Facts".

## How can configuration be modularized?
Can we use some kind of Dependency Injection to modularize our configuration?
Good Articles & Videos about:
* http://tech.puredanger.com/2014/01/03/clojure-dependency-injection/
* http://software-ninja-ninja.blogspot.de/2014/04/5-faces-of-dependency-injection-in.html
* https://www.youtube.com/watch?v=13cmHf_kt-Q

Frameworks:
* https://github.com/stuartsierra/component
* https://github.com/palletops/leaven


  
  
