# Architectural Decisions
## Separate Domain from Infrastructure
There are many reasons for separating domain from infrastructure - in case of DevOps the expense of integration tests are important. In terms of dda-pallet we use the names
* crate to describe infrastructure (as crate is defined by pallet)
* domain for domain logic
In order to do as little integration tests as possible, we will keep crates as simple as possible.

## Boundaries
For crates we've namespaces following the pattern
```
dda.pallet.crate.[crate-name]
dda.pallet.domain.[crate-name]
```
Both crate-name namespaces are the top level and the boundary to the outside. All namespaces below are for internal use only.

## Input / Output Spec
At the level of boundaries all input and output-types of functions should, if reasonable, be described by a schema and validated.

## Composition over API
If possible, we compose crates using groups :extends.
```
(api/group-spec "dda-git-group"
  :extends [(config-crate/with-config stack-config)
            git-crate/with-git])
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

## ResolveSecrets
[See ResolveSecrets](ResolveSecrets.md)

# Design Decisions
## DDD ns layout
We aim to a unified namespace layout:
```
dda.pallet.dda-xxx-crate.app
dda.pallet.dda-xxx-crate.domain
dda.pallet.dda-xxx-crate.infra
```
