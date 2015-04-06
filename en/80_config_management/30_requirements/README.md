# Requirements
Detailed and referencable requirements for this feature can be found at https://requirements.domaindrivenarchitecture.org/CmRequirementsConfiguration 

## User and Roles
* IT-Operator

##Requirements
###Validation
* UseCase0090 CM System validates configuration ahead of applying.

###Distribution
* NonFun012 Configuration Distribution
   * System pushes configuration from a central system to nodes.
      * Configuration receiver has the following prerequisites:
        * Running SSH server
        * Credentials known by configuration management system
        * Bash is available.
      * System delivers only the node specific configuration to target nodes. Other nodes security relevant stuff (like SSL keys, credentials, configuration informations) stays central.
   * Configuration for developer client nodes should be pulled from the configuration management repository. Developers should be able to apply their own configuration of their developer clients themselves.

###Dimension Configuration vs. Facts
* UseCase0091 CM System reads the version of already applied configurations from the target system.
* UseCase0092 CM System writes the version of currently applied configuration to the target system.

###Dimension Multitenancy
* NonFun024 Multitenant configuration
   * Multitenant configuration can be handled separated per tenant

%{ include "../README.md" %}
