#Version Management

As pointed out in Phases, the installation is intended to run only once. But after the first installation, the modules will evolve and get new features and improvements. 

In order to provide these changes to already installed, existing nodes, ddaBase supports versioned modules and an upgrade mechanism. The features are:
* Versions are handled on crate level. Crate versions in terms of 
  * code will be available as artifact,
  * state (installed on nodes) will provided as property in state-mgm,
  * configuration structure will be provided as property in configuration definition.
* different step sizes (with collected upgrades)