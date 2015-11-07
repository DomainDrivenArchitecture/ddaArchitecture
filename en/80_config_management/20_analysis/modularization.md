# Modularization
## How can configuration be modularized?
## Which dimensions are important for cutting off the building blocks?
There are many relevant Dimensions for cutting modules
* tenants, 
* different system environments like dev, test, staging, integration or production 
* cross cutting functions like security, backup, users identity on various levels

## Can it-ops services be abstracted and integrated?
## What kind of platforms can we distinguish?
## How can we apply same modules on different platforms?
## How can / should Configuration Management support many instances on single server?
## What elements are important for handling versions?
There will always be the situation of different versions of deployed software. Distinguishing between debit and actual. "Configuration" denominates the pursued debit, the actual state of server nodes we will name "Facts".

## Which kinds of configuration, installation or roll out jobs can we distinguish?

## How can configuration be modularized?
Can we use some kind of Dependency Injection to modularize our configuration?
Good Articles & Videos about:
* http://tech.puredanger.com/2014/01/03/clojure-dependency-injection/
* http://software-ninja-ninja.blogspot.de/2014/04/5-faces-of-dependency-injection-in.html
* https://www.youtube.com/watch?v=13cmHf_kt-Q

Frameworks:
* https://github.com/stuartsierra/component
* https://github.com/palletops/leaven


  
  
