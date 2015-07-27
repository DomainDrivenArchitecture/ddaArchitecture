# Realization

## Design Decissions
1. __ConfigurationHandOver__: Content of configuration files / script files is handed over (between functions) either as stevedore or as vector of strings. The conversion in to final single string including newlines happens as late as possible.
2. __FunctionSignatures__: We follow the clojure convention: ```
(defn function-name 
  [mandantory parameter 
  & {:keys [optional1 ... optionaln 
     :or {optional1 "Default value for optional1"
          ...}]}]
```
3. __StateHandling__: Crates tend to spread ```(stevedore/script (file-exists? ...))``` across code. In dda context we concentrate such target system state into the :settings phase on one hand and on dda-basic-crate on the other hand. 

## General Functions for DDA Modules
* Phase Support
* Report