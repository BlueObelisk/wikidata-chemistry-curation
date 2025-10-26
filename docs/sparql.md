# Wikidata-based curation approaches

## Wikidata items without SMILES

Wikipedia has a separate chemistry community, and while some Wikidata chemistry content is visible on
<a name="tp1">Wikipedia</a>, it also happens regularly that Wikipedia has a <a name="tp2">SMILES</a> for a chemical compound, where Wikidata
does not. DBpedia helps here [<a href="#citeref1">1</a>].

The following SPARQL query finds ten thousand (the default limit in <a name="tp3">DBpedia</a>) Wikipedia pages with 
a `ChemBox` and checks for those if Wikidata has a SMILES:

**SPARQL** [sparql/missingSMILES.rq](sparql/missingSMILES.code.html) ([run](https://query.wikidata.org/embed.html#PREFIX%20dbpedia2%3A%20%3Chttp%3A%2F%2Fdbpedia.org%2Fproperty%2F%3E%0A%0ASELECT%20%3Fs%20%3Farticle%20%3Fitem%20%3FitemLabel%20WITH%20%7B%0A%20%20SELECT%20DISTINCT%20%3Fs%20%3Farticle%20WHERE%20%7B%0A%20%20%20%20SERVICE%20%3Chttps%3A%2F%2Fdbpedia.org%2Fsparql%3E%20%7B%0A%20%20%20%20%20%20%3Fs%20dbpedia2%3AwikiPageUsesTemplate%20%3Chttp%3A%2F%2Fdbpedia.org%2Fresource%2FTemplate%3AChembox%3E.%0A%20%20%20%20%20%20%3Farticle_db%20foaf%3AprimaryTopic%20%3Fs.%0A%20%20%20%20%7D%0A%20%20%20%20BIND%20%28IRI%28REPLACE%28STR%28%3Farticle_db%29%2C%20%22http%3A%2F%2F%22%2C%20%22https%3A%2F%2F%22%2C%20%22i%22%29%29%20AS%20%3Farticle%29%0A%20%20%7D%0A%7D%20AS%20%25DBPEDIA%20WITH%20%7B%0A%20%20SELECT%20DISTINCT%20%3Fs%20%3Farticle%20%3Fitem%20WHERE%20%7B%0A%20%20%20%20INCLUDE%20%25DBPEDIA%0A%20%20%20%20%3Farticle%20schema%3Aabout%20%3Fitem%20.%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP233%20%5B%5D%20%7D%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP2017%20%5B%5D%20%7D%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP10718%20%5B%5D%20%7D%0A%20%20%7D%0A%7D%20AS%20%25CHEMICALS%20WHERE%20%7B%0A%20%20INCLUDE%20%25CHEMICALS%0A%20%20VALUES%20%3Fchemicals%20%7B%20wd%3AQ113145171%20wd%3AQ59199015%20%7D%0A%20%20%3Fitem%20wdt%3AP31%20%3Fchemicals.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A), [edit](https://query.wikidata.org/#PREFIX%20dbpedia2%3A%20%3Chttp%3A%2F%2Fdbpedia.org%2Fproperty%2F%3E%0A%0ASELECT%20%3Fs%20%3Farticle%20%3Fitem%20%3FitemLabel%20WITH%20%7B%0A%20%20SELECT%20DISTINCT%20%3Fs%20%3Farticle%20WHERE%20%7B%0A%20%20%20%20SERVICE%20%3Chttps%3A%2F%2Fdbpedia.org%2Fsparql%3E%20%7B%0A%20%20%20%20%20%20%3Fs%20dbpedia2%3AwikiPageUsesTemplate%20%3Chttp%3A%2F%2Fdbpedia.org%2Fresource%2FTemplate%3AChembox%3E.%0A%20%20%20%20%20%20%3Farticle_db%20foaf%3AprimaryTopic%20%3Fs.%0A%20%20%20%20%7D%0A%20%20%20%20BIND%20%28IRI%28REPLACE%28STR%28%3Farticle_db%29%2C%20%22http%3A%2F%2F%22%2C%20%22https%3A%2F%2F%22%2C%20%22i%22%29%29%20AS%20%3Farticle%29%0A%20%20%7D%0A%7D%20AS%20%25DBPEDIA%20WITH%20%7B%0A%20%20SELECT%20DISTINCT%20%3Fs%20%3Farticle%20%3Fitem%20WHERE%20%7B%0A%20%20%20%20INCLUDE%20%25DBPEDIA%0A%20%20%20%20%3Farticle%20schema%3Aabout%20%3Fitem%20.%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP233%20%5B%5D%20%7D%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP2017%20%5B%5D%20%7D%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP10718%20%5B%5D%20%7D%0A%20%20%7D%0A%7D%20AS%20%25CHEMICALS%20WHERE%20%7B%0A%20%20INCLUDE%20%25CHEMICALS%0A%20%20VALUES%20%3Fchemicals%20%7B%20wd%3AQ113145171%20wd%3AQ59199015%20%7D%0A%20%20%3Fitem%20wdt%3AP31%20%3Fchemicals.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A))

```sparql
PREFIX dbpedia2: <http://dbpedia.org/property/>
SELECT ?s ?article ?item ?itemLabel WITH {
  SELECT DISTINCT ?s ?article WHERE {
    SERVICE <https://dbpedia.org/sparql> {
      ?s dbpedia2:wikiPageUsesTemplate <http://dbpedia.org/resource/Template:Chembox>.
      ?article_db foaf:primaryTopic ?s.
    }
    BIND (IRI(REPLACE(STR(?article_db), "http://", "https://", "i")) AS ?article)
  }
} AS %DBPEDIA WITH {
  SELECT DISTINCT ?s ?article ?item WHERE {
    INCLUDE %DBPEDIA
    ?article schema:about ?item .
    MINUS { ?item wdt:P233 [] }
    MINUS { ?item wdt:P2017 [] }
    MINUS { ?item wdt:P10718 [] }
  }
} AS %CHEMICALS WHERE {
  INCLUDE %CHEMICALS
  VALUES ?chemicals { wd:Q113145171 wd:Q59199015 }
  ?item wdt:P31 ?chemicals.
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```

The results look like this:

<table>
  <tr>
    <td><b>s</b></td>
    <td><b>article</b></td>
    <td><b>item</b></td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Manganese_germanide</td>
    <td>https://en.wikipedia.org/wiki/Manganese_germanide</td>
    <td><a href="https://tools.wmflabs.org/scholia/Q97933222">Manganese germanide</a> (<a href="http://www.wikidata.org/entity/Q97933222">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_octacyanomolybdate(IV)</td>
    <td>https://en.wikipedia.org/wiki/Potassium_octacyanomolybdate(IV)</td>
    <td><a href="https://tools.wmflabs.org/scholia/Q98078085">Potassium octacyanomolybdate(IV)</a> (<a href="http://www.wikidata.org/entity/Q98078085">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Vanadium(V)_chloride_chlorimide</td>
    <td>https://en.wikipedia.org/wiki/Vanadium(V)_chloride_chlorimide</td>
    <td><a href="https://tools.wmflabs.org/scholia/Q100341984">vanadium(V) chloride chlorimide</a> (<a href="http://www.wikidata.org/entity/Q100341984">edit</a>)</td>
  </tr>
  <tr><td colspan="2"><a href="sparql/missingSMILES.code.html">sparql/missingSMILES.rq</a></td></tr>
</table>

## Polymers without CXSMILES

Many <a name="tp4">polymers</a> can have a <a name="tp5">CXSMILES</a> property and the following query lists those that do not
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

## Functional groups without CXSMILES

We can do the same thing for <a name="tp6">functional groups</a>:

**SPARQL** [sparql/functionalGroupsWithoutCXSMILES.rq](sparql/functionalGroupsWithoutCXSMILES.code.html) ([run](https://query.wikidata.org/embed.html#SELECT%20%3Ffg%20%3FfgLabel%20%3Fcxsmiles%20WHERE%20%7B%0A%20%20%3Ffg%20wdt%3AP31%2Fwdt%3AP279*%20wd%3AQ170409%20.%0A%20%20MINUS%20%7B%20%3Ffg%20wdt%3AP10718%20%3Fcxsmiles%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cmul%2Cen%22.%20%7D%0A%7D%0A), [edit](https://query.wikidata.org/#SELECT%20%3Ffg%20%3FfgLabel%20%3Fcxsmiles%20WHERE%20%7B%0A%20%20%3Ffg%20wdt%3AP31%2Fwdt%3AP279*%20wd%3AQ170409%20.%0A%20%20MINUS%20%7B%20%3Ffg%20wdt%3AP10718%20%3Fcxsmiles%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cmul%2Cen%22.%20%7D%0A%7D%0A))

```sparql
SELECT ?fg ?fgLabel ?cxsmiles WHERE {
  ?fg wdt:P31/wdt:P279* wd:Q170409 .
  MINUS { ?fg wdt:P10718 ?cxsmiles }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],mul,en". }
}
```

Here too, the list provides a list of curation opportunities:

<table>
  <tr>
    <td><b>fg</b></td>
    <td><b>cxsmiles</b></td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q2633793">acetamido group</a> (<a href="http://www.wikidata.org/entity/Q2633793">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q2633806">peroxyacetyl group</a> (<a href="http://www.wikidata.org/entity/Q2633806">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q2896782">benzhydryl</a> (<a href="http://www.wikidata.org/entity/Q2896782">edit</a>)</td>
    <td></td>
  </tr>
  <tr><td colspan="2"><a href="sparql/functionalGroupsWithoutCXSMILES.code.html">sparql/functionalGroupsWithoutCXSMILES.rq</a></td></tr>
</table>

## References

1. <a name="citeref1"></a> Auer S, Bizer C, Kobilarov G, Lehmann J, Cyganiak R, Ives Z. DBpedia: A Nucleus for a Web of Open Data. In: The Semantic Web. 2007. p. 722–35.  doi:[10.1007/978-3-540-76298-0_52](https://doi.org/10.1007/978-3-540-76298-0_52) ([Scholia](https://scholia.toolforge.org/doi/10.1007/978-3-540-76298-0_52))

