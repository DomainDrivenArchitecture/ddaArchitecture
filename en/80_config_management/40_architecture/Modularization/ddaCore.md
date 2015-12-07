#DDA Core Modules

## ddaConfiguration
A configuration
1. provides the effective Configuration and
2. validates it
for specific ExecutionContexts.

## ddaInit
The ddaInit crate  provides an unique cm environment across the different underlaying systems (dedicated node, vm, docker container, ...).

## ddaBase
The ddaBase provides 
* **Instance-Support** : The install and configuration phase, both are instance aware, so the software can be installed single or multiinstance.
* **StateManagement** : Different states will sprawl across the modules if not governed. So in DDA, the state is allowed only in one place - in the dda-base-crate. Therefore dda-base-crate reads and writes a statefile per module, where the module can manage its state.  
* **Version Management** : After the first installation the modules will evolve and get new features and improvements. In order to support all the existing nodes, ddaBase supports versioned modules and an upgrade mechanism. To support different step sizes, collected upgrades are possible.
  * Versions are handled on crate level. In code, the old version will be available as artifact, on nodes each crate will have its own state-mgm file.