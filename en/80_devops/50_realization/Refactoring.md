# Refactorings
See also [Architecture & Decission](../40_architecture/Decisions.md)

## Integration Folder
In order to separate integration tests from the rest of the codebase, we've an integration source-folder.
Integration tests may target cloud systems, pre spawned existing systems or docker containers.
We've integration tests for each complex function on the crate level.

## Docker based Integration Tests
If possible, we prefer docker based integration tests.

## Unit Tests for Domain
If there is complex logic in domain area, we will do unit tests.

## Dimension: Target
The target configuration is separated from targets content configuration.

## Short Package
We use
* `dda` instead of `org.domaindrivenarchitecture`
* `meissa` instead of `de.meissa-gmbh`

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

## social links
We will put all our social links in the readme.md of our project.
```
[![Slack](https://img.shields.io/badge/chat-clojurians-green.svg?style=flat)](https://clojurians.slack.com/messages/#dda-pallet/) | [<img src="https://domaindrivenarchitecture.org/img/meetup.svg" width=50 alt="DevOps Hacking with Clojure Meetup"> DevOps Hacking with Clojure](https://www.meetup.com/de-DE/preview/dda-pallet-DevOps-Hacking-with-Clojure) | [Website & Blog](https://domaindrivenarchitecture.org)
```
