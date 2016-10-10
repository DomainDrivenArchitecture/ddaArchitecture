#Scope
## What is the scope of Configuration Management, what are the limits?
The question is, how Configuration Management can be distinguished from things like
* windows desktop applications with their installers or
* linux packages?

Our thesis is: Configuration Management is the general unit for configuring all systems in scope. Therefore Configuration Management unites all the different ways, installers or package managers are offering.

## How can configuration be characterized?
On the one hand we follow the principle "Convention over Configuration". This means, configuration should be as easy as possible.
On the other hand a good Configuration Management System should be able to handle as many configuration details as possible. This means, we've to distinguish between the complex **System Adapters** and the modules having our conventions build in, the **Convention Modules**.

System Adapters will represent get their configuration options as configuration data. Convention Modules will convert our simplified input to the fully complex configuration data, needed by the System Adapters.

So we can say: "Configuration is Data". 

## Should Configuration be Data only?
Configuration should be data only with the only exception of referenced keys out of the Specification Key Space.
