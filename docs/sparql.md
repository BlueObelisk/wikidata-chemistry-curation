# Wikidata-based curation approaches

## Polymers without CXSMILES

Many polymers can have a CXSMILES property and the following query lists those that do not
have this property:

**SPARQL** [sparql/polymersWithoutCXSMILES.rq](sparql/polymersWithoutCXSMILES.code.html) ([run](https://query.wikidata.org/embed.html#SELECT%20%3Fcmp%20%3FcmpLabel%20WHERE%20%7B%0A%20%20%3Fcmp%20wdt%3AP31%20wd%3AQ81163%20.%0A%20%20MINUS%20%7B%20%3Fcmp%20wdt%3AP10718%20%5B%5D%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A), [edit](https://query.wikidata.org/#SELECT%20%3Fcmp%20%3FcmpLabel%20WHERE%20%7B%0A%20%20%3Fcmp%20wdt%3AP31%20wd%3AQ81163%20.%0A%20%20MINUS%20%7B%20%3Fcmp%20wdt%3AP10718%20%5B%5D%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A))

```sparql
SELECT ?cmp ?cmpLabel WHERE {
  ?cmp wdt:P31 wd:Q81163 .
  MINUS { ?cmp wdt:P10718 [] }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```

This returns values like this:

<table>
  <tr>
    <td><b>cmp</b></td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q145126">polyisoprene</a> (<a href="http://www.wikidata.org/entity/Q145126">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q146415">Styrene-acrylonitrile resin</a> (<a href="http://www.wikidata.org/entity/Q146415">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q408014">chondroitin sulfate</a> (<a href="http://www.wikidata.org/entity/Q408014">edit</a>)</td>
  </tr>
  <tr><td colspan="2"><a href="sparql/polymersWithoutCXSMILES.code.html">sparql/polymersWithoutCXSMILES.rq</a></td></tr>
</table>
