#Development
## How should we apply Configuration?
There are several ways of apply configuration to target systems. Some like puppet/augeas or famous sed lines try to change existing configuration on target system. But they will fail, if the expected configuration on target system is different to the expected one.
So changing existing configuration is not safe. A second argument against changing existent configuration is the semantic decline. Within the Configuration Management we can operate on higher level of abstraction.
 
So we tend to do a one way enforced configuration. Relevant informations from target system, called facts,  we collect in a separate phase.

## Do we represent state and how can state be managed?
If state is not managed, we will be faced with the fact that state is scattered across the whole system and module. In order to omit this scattered state, we should offer a managed way for state handling.  

## How can Configuration Management be tested?
Testing in area of Configuration Management differs in some ways from plain software testing. In Configuration Management we
* depend heavily on integration. Installation is done by a shell, provisioning is done by datacenter apis and provided packages are delivered by several artifact repositories. We well not be able to encapsulate all of these dependencies.
* can decide upon success or failure only on the targeted system.
In order to get some testing into the world of DevOps, we are distinguish between System Adapters (here we will need deep integration testing) and Convention Adapters (Data in / Data out is easy to unit test).  
 
### Test First in case of Configuration
We always try to express our expectation up front. In case of Unit Tests, that's same as in testing Software, in case of integration Testing, we describe some tests on the target system.

### Unit Testing
All data driven modules and comlplex functions will be heavily unit tested.   

### Integration Testing
All system integrating modules have to be integration tested.  

### Target System Assertions
On target systems we need a framework for expressing assertions like "is service listening on port x", "is compute started" or "is file x present". The framework will collect these facts from target system and make them available to integration testing system. 

### Software Module Compatibility Testing
For all configuration management modules compatibility is important. So we will persist planned changes to a given target as normalized intermediate format, we call this plan. So future changes can be compared against this persisted plans.

### Security Testing
TBD

## How do we handle exceptions during configuration process?
TBD