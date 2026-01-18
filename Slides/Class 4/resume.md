# RDF Schema

RDFS is used to represent light-weight ontologies in RDF, it provides a standard vocabulary to declare in RDF vocabularies to be used in RDF descriptions. It reuses the vocabulary of RDF and introduces additional constructs. An RDF vocabulary is a set of property declarations and class declarations.

It adds classes, properties and relationships. Example:

```
:Oven a rdfs:Class .
:hasTemperature rdfs:domain :Oven ;
                rdfs:range xsd:decimal .
```

It also adds domain and range for properties. It also allows subProperties and subClasses.

Essentially, RDFS adds semantic meaning to RDF triples.

- RDF = raw triples (data).
- RDFS = RDF + simple schema/vocabulary to describe the structure and meaning of those triples.