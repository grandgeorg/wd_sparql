# Zielsetzung

Welche SPARQL-Abfragen werden benötigt um nach bestimmten Kriterien Kunstwerke im Datenbestand von Wikidata zu finden?

## Suche nach Werken eines Künstlers

Es sind verschiedene Ansätze möglich. Beginnen wir mit einem Beispiel aus dem [Wikidata-Workshop von Claudia Müller-Birn](https://github.com/clmb/wikidata_workshop/tree/master/SPARQL1_Statements).

### Über die Eigenschaft Werke

Künstlern können über die Eigenschaft Werke (notable work) Kunstwerke zugewiesen werden, deren Urheber sie sind.

```sparql
SELECT ?item ?itemLabel

WHERE 
{
  wd:Q762 wdt:P800 ?item . # Leonardo da Vinci Werke
  
    SERVICE wikibase:label{ bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en" . }
}
```
[auf WDQS ausprobieren ...](https://query.wikidata.org/#%23Suche%20alle%20Gem%C3%A4lde%20eines%20K%C3%BCnstlers%0A%0ASELECT%20%3Fitem%20%3FitemLabel%0AWHERE%20%0A%7B%0A%20%20wd%3AQ762%20wdt%3AP800%20%3Fitem%20.%20%23%20Leonardo%20da%20Vinci%20Werke%0A%20%20%0A%20%20%20%20SERVICE%20wikibase%3Alabel%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22%20.%20%7D%0A%0A%7D)

Ergebnis (4.10.2018): 13 Werke

### Über die Eigenschaft Urheber

Umgekehrt ist in aller Regle bei einem Kunstwerk ein Urheber angegeben. Fragt man von dieser Seite nach Werken Leonardo da Vincis, also:

```sparql
SELECT ?item ?itemLabel 
WHERE
 {
  ?item wdt:P170 wd:Q762 . # Eigenschaft Urheber: Leonardo da Vinci
   
  SERVICE wikibase:label{ bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```
[auf WDQS ausprobieren ...](https://query.wikidata.org/#%23%20Suche%20nach%20Gem%C3%A4lden%20Leonardo%20da%20Vincis%2C%20per%20Urheber%0A%0ASELECT%20%3Fitem%20%3FitemLabel%20%0AWHERE%0A%20%7B%0A%20%20%3Fitem%20wdt%3AP170%20wd%3AQ762%20.%20%23%20Eigenschaft%20Urheber%3A%20Leonardo%20da%20Vinci%0A%20%20%20%0A%20%20SERVICE%20wikibase%3Alabel%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D)

Ergebnis (4.10.2018): 82 Werke
