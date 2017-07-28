# Processes and Phases in dda-pallet
On inspecting result in REPL you maybe wondered about terms like apply-install, apply-config, server-test or init, install or configure phases.
Phases are building blocks for our provisioning processes. In dda-pallet we use the following phases:
* **bootstrap**: Bootstrap is a convention originate from pallet. In this phase we bring up new compute services and other cloud resources.
* **settings**: Settings is a convention originate from pallet. The settings phase collects informations from server nodes (we name these informations facts) without providing side effects. So the settings phase does not alter state of servers nodes.
* **init**: Init is a dda-pallet convention. Init brings nodes to a similar starting position (e.g. across different providers). In effect the following provisioning steps will be more standardized.  
* **install**: Install is a dda-pallet convention. The install phase brings software to nodes. The installation is intended to take effect only once.
* **configure**: Configure is a convention originate from pallet. Configure brings the defined configuration to the target nodes. Configure is intended to be applied many times (at least every timy you change your configuration) and will overwrite existing changes.
* **app-rollout**: App-Rollout is a dda-pallet convention. The app-rollout phase allows to execute manual steps and is used e.g.for migrations ore more complex roll outs. The app rollout phase support automated preparation of manual roll out (e.g. download new application binaries, drivers, database migration scripts upfront).
* **test**: Test is a dda-pallet convention. The test phase is used for comparing facts collected during the setting phase against given expectations. The test phase provides no side effects.

In contrast apply-install, apply-config or server-test are predefined processes:
* **apply-install**: applies settings, init, install and configure.
* **apply-config**: applies settings and configure.
* **server-test**: applies settings and test.
