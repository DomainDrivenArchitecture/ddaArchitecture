##Configuration
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

###Dependency Injection
Good Articles & Videos about:
* http://tech.puredanger.com/2014/01/03/clojure-dependency-injection/
* http://software-ninja-ninja.blogspot.de/2014/04/5-faces-of-dependency-injection-in.html
* https://www.youtube.com/watch?v=13cmHf_kt-Q

Frameworks:
* https://github.com/stuartsierra/component
* https://github.com/palletops/leaven

  
  
