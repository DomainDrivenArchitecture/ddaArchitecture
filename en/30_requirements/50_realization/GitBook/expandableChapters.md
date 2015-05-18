# Developing GitBook extension "expandable-chapters" 

## Requirement
{% include "git+https://github.com/DomainDrivenArchitecture/ddaRequirement.git/en/requirements/req0047.md" %}

## Acceptance Criteria
1. there is a gitbook-plugin-expandable-chapters - forked from https://github.com/DomainDrivenArchitecture/gitbook-plugin-expandable-chapters.
2. there is a fork from https://github.com/DomainDrivenArchitecture/ddaArchitecture with plugin configured using "expandable-chapters" (https://github.com/DomainDrivenArchitecture/ddaArchitecture/blob/master/book.json)
3. gitbook build generates a book with exandable / collapsable chapters can be shown
4. a short webconf, explaining how the plugin is structured (language english or german).

## Setup for local GitBook publish
Our setup is (on ubuntu14.04):
 * gitbook
     * root: apt-get install npm
     * root: npm install gitbook -g
     * root: ln -s /usr/bin/nodejs /usr/bin/node
     * user: npm install gitbook-plugin-piwik
 * for editing we are using "Springs STS" other eclipse versions should work as well.