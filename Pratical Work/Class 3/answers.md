# Querying data on the Semantic Web

## Observing example queries

[Wikidata Query Service](https://query.wikidata.org/)

Looking at the cats example:

```sparql
SELECT ?item ?itemLabel
WHERE
{
  ?item wdt:P31 wd:Q146. # Must be a cat
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],mul,en". } # Helps get the label in your language, if not, then default for all languages, then en language
}
```

> Put your mouse on top of wdt:P31. What do you read? Do the same for wd:Q146. 

wdt:P31 defines that the ?item must be a instanceOf, while wd:Q146 defines a Cat class. Together they force an ?item to be an instance of the class Cat.

> What is the Q number of this entity (cow)? Execute the query. How many results there are?

Q11748378, with 18 results

> Select the example query for horses

```sparql
#Horses (showing some info about them)
# ----
# Illustrates optional fields, instances of subclasses, language fallback on label service, date to year conversion
#title: Horses on Wikidata
SELECT DISTINCT ?horse ?horseLabel ?mother ?motherLabel ?father ?fatherLabel (year(?birthdate) as ?birthyear) (year(?deathdate) as ?deathyear) ?genderLabel
WHERE
{
  ?horse wdt:P31/wdt:P279* wd:Q726 .     # Instance of and subclasses of Q726 (horse)

  OPTIONAL{?horse wdt:P25 ?mother .}     # mother
  OPTIONAL{?horse wdt:P22 ?father .}     # father
  OPTIONAL{?horse wdt:P569 ?birthdate .} # date of birth
  OPTIONAL{?horse wdt:P570 ?deathdate .} # date of death
  OPTIONAL{?horse wdt:P21 ?gender .}     # sex or gender

  SERVICE wikibase:label { #BabelRainbow
    bd:serviceParam wikibase:language "[AUTO_LANGUAGE],mul,fr,ar,be,bg,bn,ca,cs,da,de,el,en,es,et,fa,fi,he,hi,hu,hy,id,it,ja,jv,ko,nb,nl,eo,pa,pl,pt,ro,ru,sh,sk,sr,sv,sw,te,th,tr,uk,yue,vec,vi,zh"
  }
}
ORDER BY ?horse
```

This query selects distinct entities. In this case it selects instances of horses and classes that are subclasses of horses.

One thing that is interesting is that they get the horseLabel despite just defining it in the select portion.

They use the optional keyword so that if a given horse does't have any of these features the query won't break, they'll simply return empty.

> Execute the query and see what happens. Then delete the comment and execute again. What allows Wikidata to determine the location of a result?

Wikidata uses a Point(x,y) that are coordinates in the map. It probably has a backend algorithm that then easily translates this to points in a map.

> What SPARQL constructs are used here that are also SQL constructs?

Obviously the SELECT, WHERE and ORDER BY. SQL also provides a similar function from WITH (SELECT ...) AS xyz. It has other things such as COUNT and GROUP BY. Overall they are very similar, we just don't have the FROM, but the WITH could be seen as something of a FROM.

> The query "Recent events" shows other features,

```ttl
SELECT ?event ?eventLabel ?date
WITH {
  SELECT DISTINCT ?event ?date
  WHERE {
    # find events
    ?event wdt:P31/wdt:P279* wd:Q1190554.
    # with a point in time or start date
    OPTIONAL { ?event wdt:P585 ?date. }
    OPTIONAL { ?event wdt:P580 ?date. }
    # but at least one of those
    FILTER(BOUND(?date) && DATATYPE(?date) = xsd:dateTime).
    # not in the future, and not more than 31 days ago
    BIND(NOW() - ?date AS ?distance).
    FILTER(0 <= ?distance && ?distance < 31).
  }
  LIMIT 150
} AS %i
WHERE {
  INCLUDE %i
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],mul,en" . }
}
```

FILTER allows us to filter the results where ?date is a xsd:dateTime and then we also filter ?distance to be NOW() - ?date, so that if it has not happened in the last 31 days, we filter out. They also use LIMIT to limit the results to the first 150.


## Challenge yourself

> Find 50 example concepts in the DBpedia dataset.

```select distinct ?Concept where {[] a ?Concept} LIMIT 50```

> Find the resource of Madonna (the singer).

```
SELECT ?resource
WHERE {
  ?resource rdfs:label "Madonna"@en .
}
```

Result: https://dbpedia.org/page/Madonna

> List the people and their names who are born in Brussels.

```
SELECT ?person ?name
WHERE {
    ?person a foaf:Person;
        foaf:name ?name ;
        dbo:birthPlace dbr:Brussels .
}
```

> Are there people who were born in Brussels and died in Paris? (use an ASK query)

```
ASK {
    ?person dbo:birthPlace dbr:Brussels;
        dbo:deathPlace dbr:Paris .
}
```

> Find 20 people (URI and place of death) who were born in Ghent, but died elsewhere.

```
SELECT ?person ?deathPlace
WHERE {
  ?person dbo:birthPlace dbr:Ghent ;
          dbo:deathPlace ?deathPlace .
  FILTER (?deathPlace != dbr:Ghent)
}
LIMIT 20
```

> Give a list of countries and their French (‘FR’) labels

```
SELECT ?country ?label
WHERE {
  ?country a dbo:Country;
        rdfs:label ?label .
    FILTER (lang(?label) = "fr")
}
```

> Choose two cities, and make everyone born in one city know all persons born in the  other and vice versa. (use a CONSTRUCT query)

```
CONSTRUCT {
  ?person1 foaf:knows ?person2 .
  ?person2 foaf:knows ?person1 .
}
WHERE {
  ?person1 dbo:birthPlace dbr:Ghent .
  ?person2 dbo:birthPlace dbr:Paris .
  FILTER (?person1 != ?person2)
}
```