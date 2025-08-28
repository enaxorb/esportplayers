## Explore Wikidata

## Nombre total de joueurs e-sport identifiés

```sparql
SELECT (COUNT(DISTINCT ?player) AS ?totalPlayers)
WHERE {
  ?player wdt:P31 wd:Q5;              
          wdt:P106 wd:Q4379701.      
}
```

## Répartition par nationalité

```sparql
SELECT ?countryLabel (COUNT(DISTINCT ?player) AS ?nbPlayers)
WHERE {
  ?player wdt:P31 wd:Q5;
          wdt:P106 wd:Q4379701;
          wdt:P27  ?country.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr,en". }
}
GROUP BY ?countryLabel
ORDER BY DESC(?nbPlayers)
```

## Parcours académique

```sparql
SELECT ?player ?playerLabel ?school ?schoolLabel
       ?degreeLabel ?majorLabel
WHERE {

  VALUES ?occ { wd:Q1168812 wd:Q4379701 }  
  ?player wdt:P106 ?occ .

  ?player p:P69 ?edStmt .                 
  ?edStmt ps:P69 ?school .                
  OPTIONAL { ?edStmt pq:P512 ?degree . }   
  OPTIONAL { ?edStmt pq:P812 ?major . }    
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr,en". }
}
ORDER BY ?playerLabel
LIMIT 500
```

## Affiliations par équipe

```sparql
SELECT ?orgLabel (COUNT(DISTINCT ?player) AS ?nb)
WHERE {
  ?player wdt:P31 wd:Q5;
          wdt:P106 wd:Q4379701;
          wdt:P54  ?org.  
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr,en". }
}
GROUP BY ?orgLabel
ORDER BY DESC(?nb)
```

## Prix et compétitions gagnés

Prix:
```sparql
SELECT ?trophyLabel (COUNT(DISTINCT ?player) AS ?nb)
WHERE {
  ?player wdt:P31 wd:Q5;
          wdt:P106 wd:Q4379701;
          p:P166 ?stmt.     
  ?stmt ps:P166 ?trophy.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr,en". }
}
GROUP BY ?trophyLabel
ORDER BY DESC(?nb)
````

Compétition:
```sparql
SELECT ?player ?playerLabel ?tournament ?tournamentLabel
WHERE {
  VALUES ?occ { wd:Q1168812 wd:Q4379701 }
  ?player wdt:P106 ?occ .

  ?tournament wdt:P1346 ?player .

  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr,en". }
}
ORDER BY DESC(?tournament)?playerLabel
LIMIT 200
```

Nombre de compétitions gagnées par joueur:
```sparql
SELECT ?player ?playerLabel (COUNT(DISTINCT ?tournament) AS ?titles)
WHERE {
  VALUES ?occ { wd:Q1168812 wd:Q4379701 }
  ?player wdt:P106 ?occ .
  ?tournament wdt:P1346 ?player .
}
GROUP BY ?player ?playerLabel
ORDER BY DESC(?titles)
LIMIT 50
```

## Nombre de propriétés

```sparql
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT ?p ?propLabel ?eff
WHERE {
  {
    SELECT ?p (COUNT(*) AS ?eff)
    WHERE {
      ?item wdt:P31 wd:Q5;
            wdt:P106 wd:Q4379701.
      ?item ?p ?o.
    }
    GROUP BY ?p
  }
  
  ?prop wikibase:directClaim ?p .
  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}
ORDER BY DESC(?eff)
# LIMIT 20
```
