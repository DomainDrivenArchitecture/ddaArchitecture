# Coding Conventions

##Usage of Named Parameters

* We use non named parameters for mandatory parameters and
* named parameters with given default value for non mandatory ones.
* Functions should have doc comment.

## Good Example
```
(defn vhost-basic-auth-options
  "function generating the authorization part of a apache vhost definition."
  [ domain-name                                         ;; mandatory parameter 
    & {:keys [authz-options]                            ;; optional parameter
       :or {authz-options ["Require valid-user"]}}]     ;; default value for optional parameter
  {:pre [... some preconditions ...]}
```

## See also
* http://dev.clojure.org/display/community/Library+Coding+Standards
* https://github.com/bbatsov/clojure-style-guide