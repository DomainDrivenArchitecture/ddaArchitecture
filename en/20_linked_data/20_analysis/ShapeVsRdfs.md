#The SHACL Spec
* Work in Draft: https://w3c.github.io/data-shapes/shacl/
* SHACL Requirements: http://www.w3.org/TR/shacl-ucr/

#Difference with using shape
Was stands for the way proposed at chapter architecture.
would be stands for the way proposed at SHACL.

## Class definition
Was 
 ``` ... a rdfs:class```
 
 would be
 ```... a sh:ShapeClass```
 
## Properties
Was 
 ```
 ontology:hasRoleName a owl:DatatypeProperty, rdf:Property;
   rdfs:domain :Role;```

would be
```
sh:property [
		sh:predicate ex:assignedTo ;
		...```
		
## Constraints
Was 
 ```
 owl:cardinality 1 ;```

would be
```
sh:maxCount 1 ;```


#Missing feature Aggregate
See definition of Aggregate in DomainDriven Design:

* Wikipedia: http://de.wikipedia.org/wiki/Domain-Driven_Design#Bestandteile_des_Dom.C3.A4nenmodells
* Martin Fowler: martinfowler.com/bliki/DDD_Aggregate.html
* Vaughn Vernon: https://vaughnvernon.co/?p=879


