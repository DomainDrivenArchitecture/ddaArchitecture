# Architectural Decisions
## Separate Domain from Infrastructure
There are many reasons for separating domain from infrastructure - in case of DevOps the expense of integration tests are important. In terms of dda-pallet we use the names
* crate to describe infrastructure (as crate is defined by pallet)
* domain for domain logic.
In order to do as less integration test as possible, we will keep crates as simple as possible.

## Integration Folder
In order to separate integration test we've an integration source-folder.
Integration tests may target use cloud systems, pre spawned existing systems or docker containers.
We've integration tests for each complex function on crate level.

## Docker based Integration Tests
If possible, we prefere docker based integration tests.

## Unit Tests for Domain
If there are complex logic in domain area, we will do unit tests.

## Crate & Domain Boundaries
For crates we've namespaces following the pattern
```
dda.pallet.crate.[crate-name]
dda.pallet.domain.[crate-name]
```
The crate-nanme namespace is the top level and the boundary to the outside. All namespaces below are for internal use only.

## Dimension: Target
The target configuration is separated from targets content configuration.

## Input / Output Spec
At the level of boundaries all input and output should be described as schema & validated.

# Design Decisions
## Short Package
We use
* `dda` instead of `org.domaindrivenarchitecture`
* `meissa` instead of `de.meissa-gmbh`

## Composition over API
If possible, we compose crates using groups :extends.
```
(api/group-spec "dda-git-group"
  :extends [(config-crate/with-config stack-config)
            git-crate/with-git])
```

## Group based Configuration
### we use
We use group based configuration
```
{:group-specific-config   ; fixed key
  {:dda-git-group         ; name of crates group
    {:dda-git  ....       ; dda-git-crate's config - there may be other crates part of this group.
     :dda-init .... }}}
```

We specify credentials for provision in the hardware description:
```
(api/node-spec
  :image {:os-family :ubuntu
          :login-user "ubuntu"}
```
or
```
{:image {:login-user {:login "ubuntu"
                      :password "password"}}}
```

### deprecated
By using group-based configuration we replace old additional-configuration
```
{:node-specific-config           ; fixed key
  {:my-node-id                   ; nodes identifier
    (node-record/new-node        ; deprecated way of providing initial credentials & host name
      :host-name ...
      :domain-name ...
      :pallet-cm-user-name ...
      :pallet-cm-user-password ...
      :additional-config
      {:dda-git ...                ; dda-git-crate's config
       :dda-init ...}}}
```

or id based configuration.
```
{:node-specific-config           ; fixed key - deprecated
  {:my-node-id                   ; nodes identifier
    {:dda-git ...                ; dda-git-crate's config
     :dda-init ...}}}
```
