#Credentials Security Solution
## Services
We've two services providing credentials security
* encrypted-personal-credentials-service
* encrypted-admin-credentials-service

## Factors for encryption / decryption
In order to encrypt / decrypt credentials we use gnupg. So beound the pallet.jar we need additional factors to run our config management:
* the gnupg sec keyring (can be loaded from ~/.gnupg/secring.gpg, PALLET_HOME/.gnupg/secring.gpg or from classpath), 
* the passphrase, if secure key is protected (has to be provided as runtime parameter).

We use https://github.com/greglook/clj-pgp as gnupg adapter. 

## Source of credentials
We need some util function to 
* collect configuration from various places with precedence  
  * service-config from conventions-module
  * PALLET_HOME/config.clj (PALLET_HOME defaults to ~/), 
  * PALLET_HOME/services/service_name.clj,  
  * current users name & ssh credentials

Secrets are stored in schema:

```clojure
:encrpyted-credential 
  {:account "account identifier unencrypted"
   :secret "ascii armored & gpg encrypted"}
```

## Utility for manipulating credentials
* decrypt credentials & show in REPL
* encrypt credentials & show in REPL 
* store encrypted credentials,
