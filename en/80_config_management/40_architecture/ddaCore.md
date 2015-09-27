#DDA Core Modules

![Figure 1: Structure of core Elements](../resources/architecture_core_modules.png)

## Module Description
### ExecutionContext
The ExecutionContext encapsulates the state recognized for application of config management:
* pointInTime - the current world time
* organisationUnit - the organizational execution context. May be tenant or finer grained organizational units. 
* targetSystem - pallet default representation of target system facts like ip, os-type and so on.
* targetInstallationState - additional dda representation of target system's installation state.  
* targetEnvType - additional dda represantation of target environment type like dev, test, integration or production.  
 
### StateAndInstanceSupport
The StateAndInstanceSupport can 
* read/write target system's installation state &
* manage the installation & configuration of server- and instance-leveled config management specifications. 

### Configuration
Configuration can for specific ExecutionContexts
1. provide the effectiveConfiguration and
2. validate.

In addition Configuration resolves the noted overwrite hierarchy. 
