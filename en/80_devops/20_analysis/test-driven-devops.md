# Test First in case of Configuration
We always try to express our expectation up front. In case of Unit Tests, that's same as in testing Software, in case of integration Testing, we describe some tests on the target system.

## Unit Testing
All data driven modules and comlplex functions will be heavily unit tested.   

## Integration Testing
All system integrating modules have to be integration tested.  

## Target System Assertions
On target systems we need a framework for expressing assertions like "is service listening on port x", "is compute started" or "is file x present". The framework will collect these facts from target system and make them available to integration testing system.

## Software Module Compatibility Testing
For all configuration management modules compatibility is important. So we will persist planned changes to a given target as normalized intermediate format, we call this plan. So future changes can be compared against this persisted plans.

## Security Testing
TBD
