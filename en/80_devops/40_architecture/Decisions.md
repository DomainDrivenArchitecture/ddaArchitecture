# Architectural Decisions
## Separate Domain from Infrastructure
There are many reasons for separating domain from infrastructure - in case of DevOps the expense of integration tests are important. In terms of dda-pallet we use the names
* crate to describe infrastructure (as crate is defined by pallet)
* domain for domain logic
In order to do as little integration tests as possible, we will keep crates as simple as possible.

## Integration Folder
In order to separate integration tests from the rest of the codebase, we've an integration source-folder.
Integration tests may target cloud systems, pre spawned existing systems or docker containers.
We've integration tests for each complex function on the crate level.

## Docker based Integration Tests
If possible, we prefer docker based integration tests.

## Unit Tests for Domain
If there is complex logic in domain area, we will do unit tests.

## Boundaries
For crates we've namespaces following the pattern
```
dda.pallet.crate.[crate-name]
dda.pallet.domain.[crate-name]
```
Both crate-name namespaces are the top level and the boundary to the outside. All namespaces below are for internal use only.

## Dimension: Target
The target configuration is separated from targets content configuration.

## Input / Output Spec
At the level of boundaries all input and output-types of functions should, if reasonable, be described by a schema and validated.

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
By using group-based configuration, we replace old configuration
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

and also id based configuration.
```
{:node-specific-config           ; fixed key - deprecated
  {:my-node-id                   ; nodes identifier
    {:dda-git ...                ; dda-git-crate's config
     :dda-init ...}}}
```

## Use app layer
Crates reside in the infra name space and configuration conventions reside in domain name space. But at some point configuration has to be combined with the corresponding crates. Following the DDD schema, we call this area 'app'.

App typically consists of

```
(def xxxAppConfig
 {:group-specific-config
  {s/Keyword {infra/facility infra/xxxConfig}}})

(def with-xxx infra/with-xxx)

(s/defn xxx-app-configuration :- xxxAppConfig
  [domain-config :- domain/xxxConfig
   & {:keys [group-key] :or {group-key :dda-httpd-group}}]
  ...)

(s/defn xxx-group-spec
   [app-config :- xxxAppConfig]
  (api/group-spec
    (get-group-name app-config)
    :extends [(config-crate/with-config app-config)
              with-xxx])))
```

## DDD ns layout
We aim to a unified namespace layout:
```
dda.pallet.dda-xxx-crate.app
dda.pallet.dda-xxx-crate.domain
dda.pallet.dda-xxx-crate.infra
```

##  Use dda-pallet aws/existing
```
[dda.pallet.commons.aws :as cloud-target]

or

[dda.pallet.commons.existing :as cloud-target]
```
instead of `dda.cm.existing`.

## fatjar able folderstructure (fat-folder)
We have now resource and src combined into artifact folders.
```
./integration/resources (or src)
./main/resources (or src)
./test/resources (or src)
./uberjar/resources (or src)

```
Now we can see, what profile is using which folders 

|         | integration | main | test | uberjar |
|---------|-------------|------|------|---------|
| dev     | x           | x    | x    | x       |
| test    |             | x    | x    |         |
| uberjar |             | x    |      | x       |
