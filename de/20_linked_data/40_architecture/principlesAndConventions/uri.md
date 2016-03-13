# URI Conventions
## The Linked Data Platform Schema
Basically we distinguish between different types, which results in different URI schemes also:
* Ontology – Defines the structure of instances
* Instances – (e.g. documents, data rows, person ...)
* Taxonomy – (e.g. controlled vocabularies, taxonomies)
* User - users are presinced resources. Users can be used as entities for authorization.

URIs are laid out as following. The curly bracket indicates placeholders.
* http://{server_name}/ontology/{ontology_name}/{version}# 
* http://{server_name}/resource/{ontology_name}/{resource_type}/{resource_identifier}#this 
* http://{server_name}/taxonomy/{taxonomy_name}/{resource_name}#this
* http://{server_name}/user/{account_identifier}#this

URIs should be international usable. Therefore URIs language should be English by convention. The following chapters provide a more detailed explanation.

## Ontologies
Ontologies have their own namespace build by the following schema:

**http://{server_name}/ontology/{ontology_name}/{version}#**

The curly brackets indicates placeholders. Their semantic is:
* {server_name} – The name of the webserver which derefers the ontology.
* {ontology_name} – The normalized name of ontology. „Normalized“ means: No special characters, white spaces and lowercase.
* {version} – The version of ontology. The version changes whenever the ontology faces a compatibility breaking change. That’s the case, if classes or properties are deleted or renamed.

Example:
```url
http://linkeddata.domaindrivenarchitecture.org/ontology/requirements/v1#
```

URIs of classes ore properties are build up by the namespace, the hash character and the name of class or property as „Camel-Case“.

Example:
```url
http://linkeddata.domaindrivenarchitecture.org/ontology/requirements/v1#UseCase 
```

## Resoures / Instances
Instances of classes have URIs built up as follows:

**http://{server_name}/resource/{ontology_name}/{resource_type}/{resource_identifier}#this** 

The elements in curly brackets are placeholders with the following meaning: 
* {server_name} – The name of the webserver which derefers the resource/instance.
* {ontology_name} – The normalized name of the ontology that provides the first type of the instance. ‘Normalization’ in this context means no special characters, spaces and all lowercase. If resource is linked with more than one ontology (the expected scenario), than the source closest ontology should be used.
* {resource_type} – Name of the first type of an instance. This name should be equal to the hash value in the ontologies URI. 
* {resource_identifier} – The normalized name of instance. The name can be label/preferred label. „Normalized“ means: No special characters white spaces and lowercase.

Example:
```url
http://linkeddata.domaindrivenarchitecture.org/resource/requirements/UseCase/0012#this 
```

## Taxonomies
Taxonomies are Instances of classes (e.g. from skos ontology). Their URIs have the following schema:

**http://{server_name}/taxonomy/{taxonomy_name}/{resource_name}#this**

The curly brackets indicate placeholders. Their semantic is:
* {server_name} – The name of the webserver which derefers the taxonomy.
* {taxonomy_name} – The normalized name of taxonomy (e.g skos:schema). „Normalized“ means: No special characters, white spaces and lowercase.
* {resource_name} – The normalized name of instance. The name can be label/preferred label. „Normalized“ means: No special characters, white spaces and lowercase.

Example:
```url
http://linkeddata.domaindrivenarchitecture.org/taxonomy/my_glossary/usecase#this
```

## Human User Identifiers
Like any resource also human users are identified by URIs. These URIs are constructed as follows

**http://{server_name}/user/{account_identifier}#this**

The curly brackets indicates placeholders. Their semantic is:
* {server_name} – The name of the webserver which defers the resource/instance.
* {account_identifier} – The account name in lowercase.

Example:
```url
http://linkeddata.domaindrivenarchitecture.org/user/mustermannm#this
```

# Usage of dereferencable URIs 
In order to ensure full linked data functionality all URIs in an enterprise linked data environment should be dereferencable. Meaning that if an HTTP client contacts an URI via the HTTP protocoll he gets back a description of the ressource that is identified by the URI  These descriptions are provided as HTML documents that present the information to the audience in the desired format (i.e.. HTML browser -> html, RDF client -> rdf).
In order to achieve that content negotiation should established throughout the whole enterprise linked data architecture. Each HTTP client that requests an URI sends in his HTTP header what sort of documents he is expecting. Servers can then provide the corresponding response based on the the request.