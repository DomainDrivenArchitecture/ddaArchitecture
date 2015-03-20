# Requirements
Detailed and referencable requirements for this feature can be found at https://requirements.domaindrivenarchitecture.org/CmRequirementsConfiguration 

## User and Roles
* IT-Operator

## Requirements
### Validation
* UseCase0090 CM System validates configuration ahead of application.

### Versions
* UseCase0091 CM System reads version of already applied configurations from target system.
* UseCase0092 CM System writes version of currently applied configuration to target system.

### Multitenancy
* NonFun024 Multi Tenant configuration
   * Multi Tenant configuration can be handled separated per tenant
   
### Distribution
* NonFun012 Configuration Distribution
   * Config for nodes should be pushed from central instances.
     * Config receiver should not need to have java installed.
     * Security relevant stuff should stay central as possible.
   * Config for developer client nodes should be pulled from config management repository developers should be able to apply the config of their developer clients themselves.

