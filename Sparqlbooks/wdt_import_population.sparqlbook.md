## Propriétés de base: nom, genre, année de naissance

```sparql
PREFIX wd:      <http://www.wikidata.org/entity/>
PREFIX wdt:     <http://www.wikidata.org/prop/direct/>
PREFIX wikibase:<http://wikiba.se/ontology#>
PREFIX bd:      <http://www.bigdata.com/rdf#>

SELECT DISTINCT 
  ?item 
  ?itemLabel 
  ?genderLabel
  ?year 
WHERE {
  SERVICE <https://query.wikidata.org/sparql> {
    VALUES ?occ { wd:Q4379701 wd:Q1168812 }
    ?item wdt:P31 wd:Q5 ;
          wdt:P106 ?occ ;
          wdt:P21  ?gender ;
          wdt:P569 ?birthDate .
    BIND(YEAR(?birthDate) AS ?year)
    SERVICE wikibase:label { 
    bd:serviceParam wikibase:language "en" .
    }
  }

  
}
LIMIT 10
```

## Préparation pour l'import

```sparql
PREFIX wd:      <http://www.wikidata.org/entity/>
PREFIX wdt:     <http://www.wikidata.org/prop/direct/>
PREFIX rdfs:    <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf:     <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX bd:      <http://www.bigdata.com/rdf#>
PREFIX wikibase: <http://wikiba.se/ontology#>

CONSTRUCT {
  ?item rdfs:label ?itemLabel ; 
    rdf:type wd:Q5 ; 
    wdt:P21 ?gender ; 
    wdt:P569 ?birthDate ; 
    wdt:P54 ?team ; 
    wdt:P27 ?country ; 
    wdt:P2416 ?game ; 
    wdt:P8687 ?twitchFollowers ; 
    wdt:P2522 ?competitionWon ;
    wdt:P2031 ?careerStart ; 
    wdt:P69 ?school ;
    wdt:P512 ?degree .
}
WHERE {
  SERVICE <https://query.wikidata.org/sparql> {
    VALUES ?occ { wd:Q4379701 wd:Q1168812 }
    ?item wdt:P31   wd:Q5 ;
          wdt:P106  ?occ ;
          wdt:P569  ?birthDate ;
          wdt:P21   ?gender .
          OPTIONAL { ?item wdt:P54 ?team . } 
          OPTIONAL { ?item wdt:P27 ?country . } 
          OPTIONAL { ?item wdt:P2416 ?game . } 
          OPTIONAL { ?item wdt:P8687 ?twitchFollowers . } 
          OPTIONAL { ?item wdt:P2522 ?competitionWon . } 
          OPTIONAL { ?item wdt:P2031 ?careerStart . } 
          OPTIONAL { ?item wdt:P69 ?school . } 
          OPTIONAL { ?item wdt:P512 ?degree . }
    
        SERVICE wikibase:label { bd:serviceParam wikibase:language "en" }   
  }
}
LIMIT 5
```

## Import des triplés

```sparql
PREFIX wd:      <http://www.wikidata.org/entity/>
PREFIX wdt:     <http://www.wikidata.org/prop/direct/>
PREFIX wikibase:<http://wikiba.se/ontology#>
PREFIX bd:      <http://www.bigdata.com/rdf#>
PREFIX rdf:     <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs:    <http://www.w3.org/2000/01/rdf-schema#>

INSERT {
  GRAPH <https://github.com/enaxorb/esportplayers/blob/main/graphs/wikidata-imported-data.md> {
    ?item rdfs:label ?itemLabel;
          wdt:P31 wd:Q5;
          wdt:P21    ?gender ;
          wdt:P569   ?birthDate ;
          wdt:P54   ?team ;
          wdt:P27   ?country ;
          wdt:P2416 ?game ;
          wdt:P8687 ?twitchFollowers ;
          wdt:P2522 ?competitionWon;
          wdt:P2031 ?careerStart;
          wdt:P69 ?school;
          wdt:P512 ?degree.
  }
}
WHERE {
  SERVICE <https://query.wikidata.org/sparql> {
    VALUES ?occ {wd:Q4379701 wd:Q1168812}
    ?item wdt:P31 wd:Q5 ;
          wdt:P106 ?occ ;
          wdt:P569 ?birthDate ;
          wdt:P21  ?gender .
    OPTIONAL { ?item wdt:P54 ?team . }
    OPTIONAL { ?item wdt:P27 ?country . }
    OPTIONAL { ?item wdt:P2416 ?game . }
    OPTIONAL { ?item wdt:P8687 ?twitchFollowers . }
    OPTIONAL {?item wdt:P2522 ?competitionWon . }
    OPTIONAL {?item wdt:P2031 ?careerStart . }
    OPTIONAL {?item wdt:P69 ?school . }
    OPTIONAL {?item wdt:P512 ?degree . }
     OPTIONAL { ?item rdfs:label ?itemLabel . FILTER(LANG(?itemLabel) = "en") }

  }
}
```