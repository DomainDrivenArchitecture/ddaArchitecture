#Phases
Phases are the answer to the question "Which kinds of configuration, installation or rollout jobs can we distinguish?"

* **bootstrap**: Bootstrap is a pallet convention. In this phase new vms are provisioned.
* **init**: Init is a dda convention. Init configures already existing nodes for the use with pallet.  
* **settings**: Settings is a pallet convention. The settings phase collects config and other informations from crates (and nodes) without providing side effects. So the settings phase does not alter state of servers and nodes. 
* **install**: Install is a dda convention. The install phase brings software to nodes. The installation is intended to take effect only once. Functions in install-phase should be able to be called multiple times. Install uses per default the newest module version or the specified one. If install is called with a newer version, a update will be carried out.
* **configure**: Configure is a pallet convention. Configure brings the newest configuration to the target nodes. Configure is intended to be called on a regular base. Configuration will always overwrite existing changes.
* **app-rollout**: Upgrade is a dda convention. The upgrade phase compares the version installed and the version intended for configuration. If there is a difference, upgrade can apply migration scripts. Functions in upgrade-phase should be able to be called multiple times and support the simulation mode.