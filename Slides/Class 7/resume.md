# Steps to knowledge sharing

- Syntax: Common symbols and concepts
- Semantics: Agreement about their meaning
- Taxonomy: Classification of concepts
- Thesauri: Associations and Relations of concepts
- Ontologies: Rules and Knowledge about which relations are allowed and make sense

# Ontology

> Formal, explicit specification of a shared conceptualization.

Provides a specification of what exists in some domain of interest. It's something in our head, a data structure in a computer, a set of terms and relationships that we share to ensure we are communicating consistently.

We attach information to data that describe its content and meaning, with this web resources can be used by machines. Then it can be used for automation, integration and reuse across other apps.

An ontology consists of a finite list of terms (i.e. concepts) and the relationships between the terms (i.e. properties). The terms denote important concepts (classes of objects) of the domain.

An Ontology enables knowledge sharing and knowledge reuse. They capture general knowledge about a domain that is changing rarely and specify concepts and relations about which knowledge is to be accumulated and processed. They can be used to organize keywords and database concepts by capturing the semantic relationships among the keywords or among the tables and fields in a database.

We develop an ontology for:
1. Common understanding of the entities in a given domain
2. Enable reuse of data
3. Create communities of researchers

Criteria for introducing ontologies:
- Large amounts of data
- Complex data structures (inheritance, containment, many relations, ...)
- Diverse sources
- Requirement for formal proofs

# OWL Language

W3C recommendation for representing ontologies on the Web. It's a semantic markup language for defining, publishing and sharing ontologies. Contains specific constructs to represent the domain and range of properties, subclass and other axioms and constraints on the values that can be assigned to the property of an object. It's based on description logics knowledge representation formalism.

OWL extends RDFS with advanced concepts. RDFS misses cadinality restrictions, inverse, symmetric, transitive, equality, disjointness, ...

An IRI uniquely identifies a resource, but a resource can have many IRIs. OWL presents owl:sameAs to indicate two resources are the same.

# Ontology design principles

1. Clarity: Understandable for both machines and humans
2. Coherence: consistency of formal and informal layers of ontology
3. Extendibility
4. Minimal coding bias: Ontology remains on knowledge level
5. Minimal ontological commitment: only define terms that are essential
6. Proper sub-concept taxonomies