## Define values in response

```
PREFIX knora-api: <http://api.knora.org/ontology/knora-api/simple/v2#>
PREFIX incunabula: <http://0.0.0.0:3333/ontology/0803/incunabula/simple/v2#>

CONSTRUCT {

  ?myVariable knora-api:isMainResource true .
  ?myVariable incunabula:title ?title .

} WHERE {

  ?myVariable a incunabula:book .
  ?myVariable incunabula:title ?title .
  
}
```

"Ich suche nach"
- Alle Möglichkeiten für ?myVariable ````?myVariable knora-api:isMainResource true .````
- Wobei ?myvariable ein Buch von Incunabula ist ````?myVariable a incunabula:book .````
- Ausserdem möchte ich den Titel des Buches in der response haben ```?myVariable a incunabula:book .```
- Und muss das deswegen im CONSTRUCT und WHERE - Teil angeben

Ergebnis:

````
{
    "@graph": [
        {
            "@id": "http://rdfh.ch/1967a9933401",
            "@type": "incunabula:book",
            "incunabula:title": {
                "@id": "http://rdfh.ch/1967a9933401/values/4530b04dc704",
                "@type": "knora-api:TextValue",
                "knora-api:valueAsString": "Itinerarius sive peregrinarius Beatissime Virginis Marie"
            },
            "rdfs:label": "Itinerarius sive peregrinarius Beatissime Virginis Marie"
        },
        {
            "@id": "http://rdfh.ch/21abac2162",
            "@type": "incunabula:book",
            "incunabula:title": {
                "@id": "http://rdfh.ch/21abac2162/values/f76660458201",
                "@type": "knora-api:TextValue",
                "knora-api:valueAsString": "Lob der Glieder Mariens"
            },
            "rdfs:label": "Lob der Glieder Mariens"
        },
        ...
    ],
    "@context": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
        "knora-api": "http://api.knora.org/ontology/knora-api/v2#",
        "incunabula": "http://0.0.0.0:3333/ontology/0803/incunabula/v2#"
    }
}
````

Ergebnis ohne Titel in CONSTRUCT oder WHERE:

````
{
    "@graph": [
        {
            "@id": "http://rdfh.ch/1967a9933401",
            "@type": "incunabula:book",
            "rdfs:label": "Itinerarius sive peregrinarius Beatissime Virginis Marie"
        },
        {
            "@id": "http://rdfh.ch/21abac2162",
            "@type": "incunabula:book",
            "rdfs:label": "Lob der Glieder Mariens"
        },
        ...
    ],
    "@context": {
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
        "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
        "knora-api": "http://api.knora.org/ontology/knora-api/v2#",
        "incunabula": "http://0.0.0.0:3333/ontology/0803/incunabula/v2#"
    }
}
````

