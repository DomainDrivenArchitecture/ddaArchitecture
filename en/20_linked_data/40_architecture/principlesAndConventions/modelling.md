#Linked Data Publishing Principles
Beyond many other principles, we found the following very handy for the pragmatic work.
 
## Separate Ontologies and Instances
Ontologies contain classes and properties but typically no instances. In certain situations there might be exceptions from this rule. Typical examples are enumerations (e.g. the named weekdays in a calendar ontology). Ontologies have different namespaces compared to resources.

## Classify Things
Form classes, give names and description to these classes.
Class names are described in singular.
Names are written as CamelCase.
Class names start with an upper case character, properties start with a lower case character.

## Form Aggregates
In order to give hints for load/store/transact on collections of things, form aggregates as advice by DomainDrivenDesign. Aggregates always need an usage context, so different aggregates for different use cases are expected.

TODO: verify cardinality syntax

Example:
```owl
owl:cardinality 1 ;
owl:minCardinality 1 ;
owl:maxCardinality 15 ;
```

## Reuse existing Standards
There are four possibilities:
1. Direct Reuse: Use existing classes like foaf:Person. This approach makes sense for existing classes that already cover most of the required functionalities.
2. Inheritance: Create sub-classes for specialization: xxx:Person rdfs:subClassOf foaf:Person. Very useful for adding domain-specific properties to instances.
3. Rename: Mark the new class as being the same: xxx:Person owl:sameAs foaf:Person. In general this solution is discouraged: when creating new ontologies this approach does not bring any real benefit while there might be bad tool support.
4. Composition: Embed existing classes in your own new class. This approach makes sense if existing classes should be semantically composed to a new class (e.g. class OnlineAccount can reference instances with type foaf:Person and myOntology:OnlineService)

# Other LinkedData Principles
* Tim Berners Lee "four rules": http://www.w3.org/DesignIssues/LinkedData.html
* Phil Archers "Recommended URI design and management principles": http://philarcher.org/diary/2013/uripersistence/#recs
* "Linked Data Patterns" by Leigh Dodds & Ian Davis: http://patterns.dataincubator.org/book/
* W3Cs Best Practices for Publishing Linked Data: http://www.w3.org/TR/ld-bp/
* URI Guidelines for publishing Linked Datasets on data.gov.au v0.1: https://github.com/AGLDWG/TR/wiki/URI-Guidelines-for-publishing-linked-datasets-on-data.gov.au-v0.1
* W3Cs Cool URIs for the Semantic Web: http://www.w3.org/TR/cooluris/