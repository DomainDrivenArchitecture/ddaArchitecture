# Requirements
Detailed and referencable requirements for this feature can be found at https://requirements.domaindrivenarchitecture.org/CmRequirementsConfiguration 

## User and Roles
* IT-Operator

##Requirements
###Validation
* UseCase0090 CM System validates configuration ahead of applying.

###Distribution
* NonFun012 Configuration Distribution
   * Config for nodes should be pushed from central instances.
      * Config receiver should not need to have java installed.
      * As possible, security relevant stuff should stay central. (Anm.: War das damit gemeint?)
   * Config for developer client nodes should be pulled from the config management repository. Developers should be able to apply the config of their developer clients themselves.

###Dimension Configuration vs. Facts
* UseCase0091 CM System reads the version of already applied configurations from the target system.
* UseCase0092 CM System writes the version of currently applied configuration to the target system.

###Dimension Multitenancy
* NonFun024 Multitenant configuration
   * Multitenant configuration can be handled separated per tenant
