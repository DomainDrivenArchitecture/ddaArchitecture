#DDA Core Modules

![Figure 1: Structure of core Elements](https://raw.githubusercontent.com/DomainDrivenArchitecture/ddaArchitecture/master/images/80_config_management/architecture_core_modules.png)

## Fact Reader (1)
* Will read installed / upgraded versions

## Configuration (2)
* distinguishe between things to be installed and things to be blind shooted configured
* Context Configuration is defined valid for
  * valid in time
  * valid in org
  * valid for facts
  * valid for environments
* Test Validation First
  * we will have a kind of unit tests checking validity in various contexts

## Realizator (3) - applys Configuration to Target Systems
* Facts are written to target system
* Config Parameters may be determid by Execution context
  * TargetSpec
  * Organization, target systems belongs to
  * Current point in time
  * Facts read from target nodes
  * Environment-Type, target system belongs to.
* Simulation mode is one way to test application of new configurations.