#Credentials Security Solution

We've two services providing credentials security
* encrypted-personal-user-credentials-service
* encrypted-admin-credentials-service

We need some util function to 
* collect configuration from various places with precedence  
  * service-config from conventions-modue
  * PALLET_HOME/config.clj (PALLET_HOME defaults to ~/), 
  * PALLET_HOME/services/service_name.clj,  
  * current users name & ssh credentials
* decrypt credentials & show in REPL
* encrypt credentials & show in REPL 
* store encrypted credentials,

We use https://github.com/greglook/clj-pgp as pgp adapter.

Secrets are stored in schema:
:encrpyted-credential 
  {:account "account identifier unencrypted"
   :secret "ascii armored & gpg encrypted"}