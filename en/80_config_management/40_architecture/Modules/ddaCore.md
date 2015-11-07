#DDA Core Modules

![Figure 1: Structure of core Elements](../resources/architecture_core_modules.png)

## ddaConfiguration
Configuration can for specific ExecutionContexts
1. provide the effectiveConfiguration and
2. validate.

## ddaInit
The ddaInit crate provides a unique cm environment across the different underlaying systems (dedicated node, vm, docker container, ...).

## ddaBase
The ddaBase provides 
* **Instance-Support** : The install and configuration phase both are instance aware, so the software can be installed single or multiinstance.
* **StateManagement** : Different states will sprawl across the modules if not governed. So in DDA state is allowed only in one place - in the dda-base-crate. Therefore dda-base-crate reads and writes a statefile per module where module can manage it's state.  
* **Version Management** : After first installation the modules will evolve and get new features and improvements. In order to support all the existing nodes, ddaBase supports versioned modules and an upgrade mechanism. To support different step sizes collected upgrades are possible.
  * Versions are handled on crate level. In code, old version will be available as artifact, on nodes each crate will have it's own state-mgm file.