#Scope
## What is the scope of DevOps, what are the limits?
The question is, how DevOps can be distinguished from things like
* windows desktop applications with their installers or
* linux packages?

Our thesis is: DevOps is the general unit for configuring all elements (servers, networks, ...) in scope. Therefore DevOps unites all the different ways, installers or package managers are offering.

## How can configuration be characterized?
On the one hand we follow the principle "Convention over Configuration". This means, configuration should be as easy as possible.
On the other hand a good DevOps System should be able to handle as many configuration details as possible. This means, we've to distinguish between the complex **Infrastructure** and place holding our conventions, the **Domain Area**.

Infrastructure Adapters will represent get their configuration options as configuration data.
Domain Modules will convert our simplified input to the fully complex infrastructure configuration data, needed by the Infrastructure Adapters.

So for us: "Configuration is mainly Data" - but in complex scenarios we will allow access to functions and execution orders.
