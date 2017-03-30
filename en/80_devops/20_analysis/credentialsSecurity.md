#Credentials Security
## What do we need credentials for?
To give a few examples, there are probably credentials for:
* cloud-provider
  * amazon: key name & secret
* initial-server-login
  * either by password: user name & pwd
  * or by public key: authorized user name & ssh public key
* create a os-user (we should provide os-user-credentials):
  * user name, password
  * ssh public-key & private-key
  * authorized ssh public keys
  * gpg keys (private & public)
* download resources by web (basic auth)
  * apply user name & password to curl / wget
* get artefacts from m2-repositories:
  * apply user name & password to mvn / gradle / lein
* download git repos:
  * either by user name & password by http
  * or by user name & public ssh key
* owncloud service
* mail accounts
* encrypted folders
* vpns
* to be continued ...

## To whom belong these credentials?  
All accounts belong to users with the exception of initial-server-login.

## Which credentials has the highest security level?
In a common scenario, there are two kinds of credentials, with top __Sicherheitsbedarf__:
* Cloud-provider credentials, because they may affect the whole cloud data-center.
* os-user-credentials, because the may affect users communication for longe time and access for a bunch of systems.

## What's the source of credentials?
* Encrypted credentials may be stored in VCS or stored in execution environment.
* If devops is executed by a personlized user, then we can use real users ssh credentials.
* We can protect credentials by encryption. One factor should remain transient. Can be the decryption keys or the passphrase, which can be handed over at start time / runtime.

## Are there important considerations for credentials security?
* Decrypted credentials may not be logged.
* Encrypted credentials should be decrypted at the latest posible point in time.
* Credentials update should be considered.
