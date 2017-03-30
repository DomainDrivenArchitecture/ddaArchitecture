# Requirements
Requirements for a DevOps System provisioning Cloud Elements and Software on Servers.

## User and Roles
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/synthesis/configManagement/CmPersonAndRole.md" %}

## Target Systems
* System provision cloud (networks, server nodes, containers, dns, ...)
* System provision Linux server.

## Modularization
* DevOps can compose components to higher level stacks.

## Configuration
* DevOps can provide configuration as plain data to the system.
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0090.md" %}
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0184.md" %}

## Statemanagement & Version
* DevOps can define facts.
* System reads facts from target system prior configuration application.
* System reads facts from target system without side effects.

## Runtime
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0182.md" %}

## Credentials Security
### Hard Crypto
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0227.md" %}
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0228.md" %}

### Configuration Sources
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0226.md" %}
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0229.md" %}
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0230.md" %}

## System Security
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0231.md" %}
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0232.md" %}
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0233.md" %}
