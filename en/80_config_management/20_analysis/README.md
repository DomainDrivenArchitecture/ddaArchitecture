# Analysis

##Business Value of Config Management
* Standardize system setup - that's good for
  * increase environmental control - new insights will result in a continuous progress
  * all installed systems will benefit simultaneously from new insights
  * systems can be installed repeatable - so testing in test systems become more meaningful
* Increase automation - that's good for
  * hide a huge number of boring details
  * react fast on tasks like setup of new systems or apply a new configuration
  * handle more systems with less human operators  

##Limits & Scoping
The question is, how config management can be distinguished from things like
* windows desktop applications with their installers or
* linux packages?

My thesis is: Config Management is the general unit for configuring all systems in scope 


##Important Insights
###Dimensions
There are many relevant Dimensions for cutting modules
* tenants, 
* different system environments like dev, test, staging, integration or production * cross cutting aspects like security, backup, users identity on various levels

###Versions matters
There will always be the situation of different versions of deployed software. Distinguishing between debit and actual.

  * On the one hand, configuration will describe the debit side. 
  * On the other hand we take also care of the actual side on server also. We will name this "facts".

Tests of configurations

Configuration can be distributed in push mode
* Push is important for security reason (server-credentials may not reside on every server node in net)
  
Configuration can be distributed in pull mode. Pull is important for social & technical reasons.
* Technical: Some networks may be not accessible from outside.
* Social: Developers don't like uncontrolled updates from outside.

Configuration is different for each system.

Configuration is quite complex.

  
  
