# GravSearch Notes

## First successfull request
Make sure you have incunabula data in Knora, if in doubt execute the following script once more:<pre>./webapi/scripts/graphdb-free-init-knora-test.sh</pre>

In Postman, create the following request (you can leave the comments in the body of the request, it will work with them included as well) :

 - Adress: <pre> http://0.0.0.0:3333/v2/searchextended </pre>
 - Headers: <pre>Key: Content-Type | Value: text/plain</pre>
 - Body for the request "return all the resources of the resource - type incunabula:page":
 
```
#
# 1. Define prefixes that you will use in the query 
#

# Define that you would like to use the simple API for now:
PREFIX knora-api: <http://api.knora.org/ontology/knora-api/simple/v2#>

# Define a prefix for the project/s that you would like to include
PREFIX incunabula: <http://0.0.0.0:3333/ontology/0803/incunabula/simple/v2#>

#
# 2. Define the Query. 
#

# Every Query has to have at least a Construct and a Where, in the construct you must define the knora-api:isMainResource.
# In the Construct is defined which values you would like to get as a response
CONSTRUCT {

  # ?myVariable is a variable, it describes the result that we don't know yet
  ?myVariable knora-api:isMainResource true ;

} WHERE {

  # The variable/s that you used must be defined in a way. This phrase defines that the variable ?myVariable is a resource of the Type incunabula:page
  ?myVariable a incunabula:page .
  
}
```
- Same body without comments:

```
PREFIX knora-api: <http://api.knora.org/ontology/knora-api/simple/v2#>
PREFIX incunabula: <http://0.0.0.0:3333/ontology/0803/incunabula/simple/v2#>

CONSTRUCT {

  ?myVariable knora-api:isMainResource true ;

} WHERE {

  ?myVariable a incunabula:page .
  
}
```
- The result should look like the following:

```
{
    "@graph": [
        {
            "@id": "http://rdfh.ch/00014b43f902",
            "@type": "incunabula:page",
            "rdfs:label": "t8r"
        },
        {
            "@id": "http://rdfh.ch/0015627fe303",
            "@type": "incunabula:page",
            "rdfs:label": "m8v"
        },
        {
            "@id": "http://rdfh.ch/0016adc2dc06",
            "@type": "incunabula:page",
            "rdfs:label": "e3r"
        },
        {
            "@id": "http://rdfh.ch/00282e78d401",
            "@type": "incunabula:page",
            "rdfs:label": "i5r"
        },
        {
            "@id": "http://rdfh.ch/003c45b4be02",
            "@type": "incunabula:page",
            "rdfs:label": "c8r"
        },
        {
            "@id": "http://rdfh.ch/00505cf0a803",
            "@type": "incunabula:page",
            "rdfs:label": "p7v"
        },
        {
            "@id": "http://rdfh.ch/006328e99901",
            "@type": "incunabula:page",
            "rdfs:label": "a6v"
        },
        {
            "@id": "http://rdfh.ch/008b56616e03",
            "@type": "incunabula:page",
            "rdfs:label": "u4v"
        },
        {
            "@id": "http://rdfh.ch/009e225a5f01",
            "@type": "incunabula:page",
            "rdfs:label": "m3v"
        },
        {
            "@id": "http://rdfh.ch/00b239964902",
            "@type": "incunabula:page",
            "rdfs:label": "i4r"
        },
        {
            "@id": "http://rdfh.ch/00c5058f3a",
            "@type": "incunabula:page",
            "rdfs:label": "r1r"
        },
        {
            "@id": "http://rdfh.ch/00c650d23303",
            "@type": "incunabula:page",
            "rdfs:label": "d4v"
        },
        {
            "@id": "http://rdfh.ch/00d91ccb2401",
            "@type": "incunabula:page",
            "rdfs:label": "m2r"
        },
        {
            "@id": "http://rdfh.ch/00da670e1e04",
            "@type": "incunabula:page",
            "rdfs:label": "125"
        },
        {
            "@id": "http://rdfh.ch/00ed33070f02",
            "@type": "incunabula:page",
            "rdfs:label": "C5r"
        },
        {
            "@id": "http://rdfh.ch/011049883d",
            "@type": "incunabula:page",
            "rdfs:label": "r7v"
        },
        {
            "@id": "http://rdfh.ch/011194cb3603",
            "@type": "incunabula:page",
            "rdfs:label": "e3r"
        },
        {
            "@id": "http://rdfh.ch/012460c42701",
            "@type": "incunabula:page",
            "rdfs:label": "m8v"
        },
        {
            "@id": "http://rdfh.ch/0125ab072104",
            "@type": "incunabula:page",
            "rdfs:label": "138"
        },
        {
            "@id": "http://rdfh.ch/013877001202",
            "@type": "incunabula:page",
            "rdfs:label": "D3v"
        },
        {
            "@id": "http://rdfh.ch/014b43f902",
            "@type": "incunabula:page",
            "rdfs:label": "a6v"
        },
        {
            "@id": "http://rdfh.ch/014c8e3cfc02",
            "@type": "incunabula:page",
            "rdfs:label": "v6v"
        },
        {
            "@id": "http://rdfh.ch/0160a578e603",
            "@type": "incunabula:page",
            "rdfs:label": "n7r"
        },
        {
            "@id": "http://rdfh.ch/0161f0bbdf06",
            "@type": "incunabula:page",
            "rdfs:label": "A3r"
        },
        {
            "@id": "http://rdfh.ch/01737171d701",
            "@type": "incunabula:page",
            "rdfs:label": "k3v"
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


## First experiments
- Check out which results you get if you change the resource type (You can see which resource types inclunabula has [here](https://github.com/dhlab-basel/Knora/blob/develop/webapi/_test_data/ontologies/incunabula-onto.ttl) )
- For instance change incunabula:page to incunabula:book or incunabula:Sideband