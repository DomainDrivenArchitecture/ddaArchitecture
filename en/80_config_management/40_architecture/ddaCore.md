#DDA Core Modules

![Figure 1: Structure of core Elements](../resources/architecture_core_modules.png)

## ddaInit
The ddaInit crate provides a unique cm environment across the diferent underlaying systems (dedicated node, vm, docker container, ...).

## ddaBase
The ddaBase provides 
* **Instance-Support** : The install and configuration phase both are instance aware, so the software can be installed single or multiinstance.
* **StateManagement** : Different states will sprawl across the modules if not governed. So in DDA state is allowed only in one place - in the dda-base-crate. Therefore dda-base-crate reads and writes a statefile per module where module can manage it's state.  
* **Version Management** : After first installation the modules will evolve and get new features and improvements. In order to support all the existing nodes, ddaBase supports versioned modules and an upgrade mechanism. To support different step sizes collected upgrades are possible.

## ddaConfiguration
Configuration can for specific ExecutionContexts
1. provide the effectiveConfiguration and
2. validate.

TODO: Describe the overwrite hierarchy.


# TBD
## ExecutionContext
The ExecutionContext encapsulates the state recognized for application of config management:
* pointInTime - the current world time
* organisationUnit - the organizational execution context. May be tenant or finer grained organizational units. 
* targetSystem - pallet default representation of target system facts like ip, os-type and so on.
* targetInstallationState - additional dda representation of target system's installation state.  
* targetEnvType - additional dda represantation of target environment type like dev, test, integration or production.  