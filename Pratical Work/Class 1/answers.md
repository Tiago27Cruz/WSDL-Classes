# Exercise 1

## 1.3 (...) What is this page describing?

This pages describes Tim Berners-Lee, creator of the World Wide Web. It has many RDF properties that describe him.

## 1.4 Try to figure out the triples that are shown there. Give 3 examples of RDF triples (each on a different line in your text file) observed in this file. Write them in Turtle format.

dbp:Tim_Berners-Lee a dbo:animal ;
    dbo:alias "TBL"@en ;
    dbo:birthPlace dbr:London ;
    dbp:birthName "1955-06-08"^^xsd:date .

## 1.5 What kind of information does this property provide?

This property provides information regarding the birth date of an dbo:Animal with a value in xsd:date. It is a functional property, therefore we know an animal can only have an unique value in this property.

## 1.6  What does it mean when the value is a hyperlink?

When a value is a hyperlink it's because it's linked data, meaning, this is not a literal value, but another entity that is being used as a value.

## 1.7 (...) Write this URL in your text file

http://dbpedia.org/property/education

## 1.8 Why are they different? What does the address on the link represent about what the address to which you are redirected to?

For me they are the same, but if they were different I could assume one is the URI (static, permanent) or PURL (permanent URL), which represents the entity itself, disregarding temporary website domain. On the other hand, the URL in the address bar is simply an URL that displays the webpage for the property.

## 1.9 Consider the Property dbp:birthPlace. What is the number in the Value column? What does the text between brackets represent? Take a look at dbp:children. What does the value formally represent? What is its type?

Well, there is no number in ``London, England (en)``, but the text between brackets specifies the language of the text field. In birthYear ``1955-01-01 (xsd:gYear)`` we have numbers and something in brackets, in this case the number represents the birth year, it is in the yyyy-mm-dd format to uphold to standards, but the data type, in this case xsd:gYear specifies that in this case, only the year matters.

dbp:children represents the number of children he has. In this case he has 2 children directly, and 3 step-children, therefore the separation.

## 1.11 Find RDF files that describe Tim Berners-Lee at the Deutsche National Bibliothek, and at the BBC

https://data.bibliotheken.nl/KB/Production/browser?resource=http%3A%2F%2Fdata.bibliotheken.nl%2Fid%2Fthes%2Fp193462516

http://www.bbc.co.uk/things/2166d5db-3cd1-4d8a-a066-bddb220ef216#id

# 2 

## 2.1 IRI that represents yourself
me:TiagoCruz

## 2.2 Define yourself as a foaf:Person, and add other relevant classes that describe you

me:TiagoCruz a foaf:Person ;
    a foaf:Student ;
    a foaf:Man ;

## 2.3 Enrich Your RDF Profile with Interests and Projects

me:TiagoCruz a foaf:Person ;
    a foaf:Student ;
    a foaf:Man ;
    foaf:interest <http://dbpedia.org/resource/Semantic_Web> .

## 2.4 Add Personal Information (Names, Affiliations)

me:TiagoCruz a foaf:Person ;
    a foaf:Student ;
    a foaf:Man ;
    foaf:interest <http://dbpedia.org/resource/Semantic_Web> ;
    foaf:name "Tiago Cruz" ;
    foaf:nick "Tuagi" ;
    me:affiliatedWith me:FEUP .

## 2.5 Include Additional Details About Yourself

me:TiagoCruz a foaf:Person ;
    a foaf:Student ;
    a foaf:Man ;
    foaf:interest <http://dbpedia.org/resource/Semantic_Web> ;
    foaf:name "Tiago Cruz" ;
    foaf:nick "Tuagi" ;
    me:affiliatedWith me:FEUP ;
    me:girlfriend me:RuteGomes .

## 2.6 Indicate Connections with Others

me:TiagoCruz a foaf:Person ;
    a foaf:Student ;
    a foaf:Man ;
    foaf:interest <http://dbpedia.org/resource/Semantic_Web> ;
    foaf:name "Tiago Cruz" ;
    foaf:nick "Tuagi" ;
    me:affiliatedWith me:FEUP ;
    me:girlfriend me:RuteGomes ;
    foaf:knows [
        me:RuteGomes
    ],
    [
        me:JohnDoe
    ] .

## 2.7 Express Your Status as a Student

me:TiagoCruz a foaf:Person ;
    a foaf:Student ;
    a foaf:Man ;
    foaf:interest <http://dbpedia.org/resource/Semantic_Web> ;
    foaf:name "Tiago Cruz" ;
    foaf:nick "Tuagi" ;
    me:affiliatedWith me:FEUP ;
    me:girlfriend me:RuteGomes ;
    foaf:knows [
        me:RuteGomes
    ],
    [
        me:JohnDoe
    ] ;
    me:studentStatus [
        me:degree "Master" ;
        me:startedOn "September 2024" .
    ] .