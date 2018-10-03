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
[auf WDQS ausprobieren ...](http://tinyurl.com/y8rw58wb)
