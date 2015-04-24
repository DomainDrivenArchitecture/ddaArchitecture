# Modelling Conventions
## Add Label and Comment
Each class or property must have an English label / comment without a language tag (default label). Language tagged labels can be added also.

## List owl and rdf Types explicitly
As a hint or help for tools that might not be able to interpret owl the associated rdf type is listed, too.

## Add cardinality to Properties
As mentionend in [modelling.md#FormAggregates]

## Add defines & isDefinedBy: .
In order to increase the human readability add defines & isDefinedBy. So readers will find an overview from detail and details from top level.

Example:
```owl
ontology:
	<https://open.vocab.org/terms/defines> ontology:hasRoleName;

ontology:hasRoleName
…
rdfs:isDefinedBy ontology: .
```

## Condensed Example

```owl
ontology:
	<https://open.vocab.org/terms/defines> ontology:hasRoleName

ontology:hasRoleName
  a owl:DatatypeProperty, rdf:Property ;
  rdfs:subPropertyOf rdfs:label ;
  rdfs:label "Role Name" ;
  rdfs:label "Role Name" @en ;
  rdfs:label "Rollenname" @de ;
  rdfs:comment "The name of the role." ;
  rdfs:comment "The name of the role."@en ;
  rdfs:comment "Der Name der Rolle."@de ;
  rdfs:domain :Role ;
  rdfs:range xsd:string;
  owl:cardinality 1 ;
  rdfs:isDefinedBy ontology: .
```

# Technical Conventions
## Turtle Format
Ontologies are stored and exchanged in turtle format.

## Namespace Storage
Elements of differnt namespaces are stored in 
* different named graphs or 
* different turtle files.