Class 2 - Introduction pt.II + Real-World Application

# Key Concepts

**Web Semantics:** Turning the web into a database through structured, meaningful data. Phrases like "Rute is beautiful" does't give a computer much meaning. On the other hand, in triple format (Rute, is, Beautiful), using the appropriate terms, the computer is able to fully understand.

**Linked Data:** Connecting data across different domains for more meaningful, interoperable use. Let's say I have "Rute is beautiful", the computer does't know who Rute is. If it's linked to other DBs such as WikiData, then the computer knows which Rute is considered beautiful.

# Web Semantic

Gives meaning to data (metadata).

Key Technologies:
- RDF (Resource Description Framework)
- OWL (Web Ontology Language)
- SPARQL

# Linked Data

Follows Tim Berners-Lee's 4 Principles:

1. Use Uniform Resource Identifiers (URI) to identify resources. (Doesn't have to be a working URL, can be like ``http://www.example.org/onto/myonto#class``)
2. Use HTTP URIs so people can look up data (It's better if it connects to something on the Web so people can understand it's definition and how to re-use it).
3. Provide useful information in standard formats (RDF).
4. Include links to other URIs to connect data.

# Real-World Applications

1. **Wikidata:** linking diverse knowledge, open, heavily used in downstream AIs, tools.
2. **Schema.org:** used in search engines for structured data; markup on the Web
3. **Enterprise Knowledge Graphs:** internal knowledge management in companies (e.g. Google 
Knowledge Graph / Microsoft / Amazon / financial / biotech).
4. **Biomedical Knowledge Graphs:** for drug discovery, disease mapping, patient data, research 
literature.
5. **Semantic search / QA systems:** systems that answer questions over linked data (e.g. 
DBpedia SPARQL endpoint, or hybrid systems combining Knowledge Graphs + text).
6. **Provenance / Trust systems:** act-checking, supply chain traceability, data governance tools