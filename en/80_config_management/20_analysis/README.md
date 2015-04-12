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

My thesis is: Config Management is the general unit for configuring all systems in scope. Therefore Config Management includes all the different installers or package managers.

##Important Thoughts
###Dimensions
There are many relevant Dimensions for cutting modules
* tenants, 
* different system environments like dev, test, staging, integration or production 
* cross cutting functions like security, backup, users identity on various levels

###Versions matters
There will always be the situation of different versions of deployed software. Distinguishing between debit and actual. "Configuration" denominates the pursued debit, the actual state of server nodes we will name "Facts".

###Test First in case of Configuration
As for every software development job, testing is essential. Therefore a kind of Test First procedure is also important for Config Management.

###Distribution
Configuration can be distributed in push mode and pull mode.
* Push is important for security reason (server-credentials may not reside on every server node in net)
* Pull is important for social & technical reasons.
  * Technical: Some networks may be not accessible from outside.
  * Social: Developers don't like uncontrolled updates from outside.

###Configuration differs
Configuration is different for each system. In the one hand this statement is trivial, on the other hand this fact is a problem for a steady quality. Test first will be of limited use here only.

###Configuration is complex
Configuration tend to be complex. Because of all the abstracted away details we have more speed, but also higher complexity to tackle with.

  
  
