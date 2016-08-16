#Credentials Security
* Credentials are for:
  * cloud-provider
    * amazon: key name & secret
  * initial-server-login
    * either user name & pwd
  * personalized-server-login
    * or authorized user name & ssh public key
  * create a os-user (primary-os-user-credentials):
    * user name, password
    * ssh public-key & private-key
    * authorized ssh public keys
  * download resources by web (basic auth)
    * apply user name & password to curl / wget
  * resolve artefacts:
    * apply user name & password to mvn / gradle / lein
  * download git repos:
    * either by user name & password by http 
    * or by user name & public ssh key
  * owncloud service
  * mail accounts
  * encrypted folders
  
All accounts belong to users with the exception of initial-server-login.

Cloud-provider- and primary-os-user-credentials are top-secret.

If config management is executed by a real user, then we can use real users ssh credentials if there are no ssh credentials configured.