# Resolving Secrets

Credentials in applications play an important role for authorization and authentication. Some credentials can be public, e.g. public keys. Credentials that are required to be private for security reasons are also called "secrets". 

Applications need to be able to access secrets in a machine-readable form, for example as a value of the type "string". However, it's usually not recommended to include a readable string-value of a secret in the code, as this would expose the secret and would result in a security hazard. As an alternative secrets can be included in the code as encrypted values or can be retrieved from another (secure) location. 

To get the the clear secrets from encrypted secrets or based on other information provided is called "resolving secrets". This chapter provides information about the possibilities to provide secrets and how secrets are resolved in dda-pallet. 

According to the dda-pallet architecture secrets are usually defined in the domain configuration. There are several possibilities to include the secrets in the configuration:
1. As plain text - can be handy for testing purposes, but should never be used in a production environment
2. As a hashed password
3. As a defined location in the password-store

Furthermore dda-pallet supports 2 different types of secret structures in the password-store: 
1. single-line secrets such as userids, passwords, SSH keys
2. multi-line secrets such as GPG keys.

During application execution the secrets are resolved in an early stage in the app layer of a crate. The function "resolve-secrets" converts the domain configuration with unresolved secrets into a configuration with resolved secrets, represented as string values. The resolved domain configuration can then directly be used by the rest of the application, for example by sub-crates. This means that later on in the code execution there is no more need for handling unresolved secrets nor caring about resolving.

The picture below shows how secrets are resolved in a crate.

![](https://github.com/DomainDrivenArchitecture/ddaArchitecture/blob/configmanagement/en/80_devops/resources/dda-secrets-and-resolving-4.svg "Resolving of secrets in dda-pallet")
