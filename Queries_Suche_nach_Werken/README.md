# Zielsetzung

Welche SPARQL-Abfragen werden benötigt um nach bestimmten Kriterien Kunstwerke im Datenbestand von Wikidata zu finden?

## Test Formatierung

```sparql
SELECT ?item
WHERE
{
  wd:Q762 wdt:P800 ?item.
}
```
[auf WDQS ausprobieren ...](https://query.wikidata.org/sparql?query=%23%20eine%20Testabfrage%20in%20Sachen%20Try-it-Link%0ASELECT%20%3Fitem%0AWHERE%0A%7B%0A%20%20wd%3AQ762%20wdt%3AP800%20%3Fitem.%0A%7D)
