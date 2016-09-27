#Credentials Security
## What do we need credentials for?
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

## To whom belong these credentials?  
All accounts belong to users with the exception of initial-server-login.

## Which credentials are top secret?
Cloud-provider- and primary-os-user-credentials are top-secret.

## What's the source of credentials?
* Encrypted credentials may be stored in VCS or stored in execution environment.
* If config management is executed by a real user, then we can use real users ssh credentials.
* We can protect credentials by encryption. Encryption keys have to be located in the execution environment.
* Keys can be locked by a passphrase, the passphrase should be transient on be handed over on runtime.

## Are there important considerations vor credentials security?
* Decrypted credentials may not be logged.
* Encrypted credentials should be decrypted at the latest posible point in time.
