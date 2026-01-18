# Web Today

The web today is mostly for human use, with no proper structure. Imagine a blog with bunch of publications, it's human-readable but not very computer friendly. This brings a series of limitations for Web Search, such as:
- High Recall, Low Precision; 
- Results highly sensitive to vocabulary;
- Results are single web pages;
- Not able to allow logical reasoning and question answering.

# RDF (Resource Description Framework)

RDF is a data model, the standard of W3C, a language to represent resources.

It's represented as triples: ``<subject, property, object>``, example: ``<“Mozart”, composed, “The Magic Flute”>``. Also called a statement.

RDF is machine-readable and structured as an oriented labeled multigraph, where both Subject and Object are nodes and property are edges. Object can be a resource or a literal.

The core features of RDF are:
- Identify things (resources)
- Express relations between things (properties)

Additional important features are:
- Assign data values to things (literals)
- Organize things in categories (i.e., classes or types)
- Add simple knowledge about categories and relations

Every resource has a URI (Universal Resource Identifier) or IRI (Internationalized Resource Identifier). An URI/IRI identifies things but may be used as a locator (URL, a web 
address) at the same time; An identifier does not necessarily enable access to a resource.

It's best to reuse an existing IRI (e.g., from a national library), but we can create our own. We should use HTTP IRIs with a namespace under our control. Hint: Cool URIs don't change.

Predicates can be both a characteristic of the resource (hasValue 123) or a relationship link between resources (Rute studiesAt FMDUP).

RDF is not a database or data file format, therefore machines need an RDF serialization, a method of transmitting or storing the information about the triples in the graph as a file.

