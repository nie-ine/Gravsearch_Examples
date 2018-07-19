## Beispiel request:

```
PREFIX knora-api: <http://api.knora.org/ontology/knora-api/simple/v2#>
PREFIX incunabula: <http://0.0.0.0:3333/ontology/0803/incunabula/simple/v2#>

CONSTRUCT {

  ?myVariable knora-api:isMainResource true ;

} WHERE {

  ?myVariable a incunabula:book .
  ?myVariable incunabula:title ?title .
  FILTER(?title = "Zeitglöcklein des Lebens und Leidens Christi")
  
}
```

"Ich suche nach.."

 - der Lösung einer Variable ?myVariable ``` ?myVariable knora-api:isMainResource true ; ```
 - wobei diese Variable ein incunabula:book ist ``` ?myVariable a incunabula:book . ```
 - und dieses buch einen titel hat ```?myVariable incunabula:title ?title .```
 - wobei der Titel gefiltert wird ``` FILTER(?title = "Zeitglöcklein des Lebens und Leidens Christi") ```
 
 
 Ergebnis: 
 
 ```
 {
     "@graph": [
         {
             "@id": "http://rdfh.ch/c5058f3a",
             "@type": "incunabula:book",
             "rdfs:label": "Zeitglöcklein des Lebens und Leidens Christi"
         },
         {
             "@id": "http://rdfh.ch/ff17e5ef9601",
             "@type": "incunabula:book",
             "rdfs:label": "Zeitglöcklein des Lebens und Leidens Christi"
         }
     ],
     "@context": {
         "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
         "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
         "knora-api": "http://api.knora.org/ontology/knora-api/v2#",
         "incunabula": "http://0.0.0.0:3333/ontology/0803/incunabula/v2#"
     }
 }
 ```
 
 Here the type of ?title is xsd:string.
 
 The following Knora value types can be compared with literals in FILTER expressions in the simple schema:
 
 - Text values (xsd:string)
 - Uri values (xsd:anyURI)
 - Integer values (xsd:integer)
 - Decimal values (xsd:decimal)
 - Boolean values (xsd:boolean)
 - Date values (knora-api:Date)