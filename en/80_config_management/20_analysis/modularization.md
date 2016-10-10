# Modularization
## How can the configuration be modularized?
The answer to this question depends on the underlying DevOps system. We can use any modularization concept provided. In case of pallet, we can use the whole abilities of clojure. So we can build modules, build artifacts, release them, sign them and reuse them by a full build system.

## Which dimensions are important for cutting off the building blocks?
There are many aspects fur cutting modules and configuration along. We call them domain dimensions. In case of Configuration Management we know the following dimensions:
* tenants 
* different system environments like dev, test, staging, integration or production 
* cross cutting functions like security, backup, user identity on various levels
* operating systems
* cloud / hosting providers
* cloud provider types
* container types
* application tiers like web, app or persistence 

## Can it-ops services be abstracted and integrated?
Ops Services are services like monitoring, alerting, backup, security testing, hardening, dns, firewalls, vpn, routing, providing compute capacity and providing a datacenter api. The the question of abstraction can be answered, if we are able to abstract differences across all known providers for each category.    

## How can we apply the same modules on different platforms?
We have to build in cross cutting features across all relevant system adapters. 
In order to support an additional distribution we have to implement the additional distribution support into all linux related System Adapters. For supporting a new Cloud Provider, we've to implement the provider support for the whole data center api System Adapters.

## How can / should Configuration Management support many instances on a single server?
Following the principle "Keep solutions as simple as possible" we should always try to keep System Adapters simple also. Multi-instance could be realized by container in most cases.

## What elements are important for handling versions?
Again with the "Keep solutions as simple as possible" principle in mind, we tend to throw old installations away an replace them with new ones over doing a upgrade. In this case, we've to transport & migrate the persisted data.

## Some more ideas:
Can we use some kind of Dependency Injection to modularize our configuration?
Good Articles & Videos about:
* http://tech.puredanger.com/2014/01/03/clojure-dependency-injection/
* http://software-ninja-ninja.blogspot.de/2014/04/5-faces-of-dependency-injection-in.html
* https://www.youtube.com/watch?v=13cmHf_kt-Q

Frameworks:
* https://github.com/stuartsierra/component
* https://github.com/palletops/leaven


  
  
