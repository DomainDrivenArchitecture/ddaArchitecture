# Realization

## Design Decissions
1. __ConfigurationHandOver__: Content of configuration files / script files is handed over (between functions) either as stevedore or as vector of strings. The conversion in to final single string including newlines happens as late as possible.
