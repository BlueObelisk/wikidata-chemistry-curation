# missingSMILES.rq
**Code examples:** [curl](#curl)
### SPARQL
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
[Execute](https://query.wikidata.org/embed.html#PREFIX%20dbpedia2%3A%20%3Chttp%3A%2F%2Fdbpedia.org%2Fproperty%2F%3E%0A%0ASELECT%20%3Fs%20%3Farticle%20%3Fitem%20%3FitemLabel%20WITH%20%7B%0A%20%20SELECT%20DISTINCT%20%3Fs%20%3Farticle%20WHERE%20%7B%0A%20%20%20%20SERVICE%20%3Chttps%3A%2F%2Fdbpedia.org%2Fsparql%3E%20%7B%0A%20%20%20%20%20%20%3Fs%20dbpedia2%3AwikiPageUsesTemplate%20%3Chttp%3A%2F%2Fdbpedia.org%2Fresource%2FTemplate%3AChembox%3E.%0A%20%20%20%20%20%20%3Farticle_db%20foaf%3AprimaryTopic%20%3Fs.%0A%20%20%20%20%7D%0A%20%20%20%20BIND%20%28IRI%28REPLACE%28STR%28%3Farticle_db%29%2C%20%22http%3A%2F%2F%22%2C%20%22https%3A%2F%2F%22%2C%20%22i%22%29%29%20AS%20%3Farticle%29%0A%20%20%7D%0A%7D%20AS%20%25DBPEDIA%20WITH%20%7B%0A%20%20SELECT%20DISTINCT%20%3Fs%20%3Farticle%20%3Fitem%20WHERE%20%7B%0A%20%20%20%20INCLUDE%20%25DBPEDIA%0A%20%20%20%20%3Farticle%20schema%3Aabout%20%3Fitem%20.%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP233%20%5B%5D%20%7D%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP2017%20%5B%5D%20%7D%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP10718%20%5B%5D%20%7D%0A%20%20%7D%0A%7D%20AS%20%25CHEMICALS%20WHERE%20%7B%0A%20%20INCLUDE%20%25CHEMICALS%0A%20%20VALUES%20%3Fchemicals%20%7B%20wd%3AQ113145171%20wd%3AQ59199015%20%7D%0A%20%20%3Fitem%20wdt%3AP31%20%3Fchemicals.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A) or [Edit](https://query.wikidata.org/#PREFIX%20dbpedia2%3A%20%3Chttp%3A%2F%2Fdbpedia.org%2Fproperty%2F%3E%0A%0ASELECT%20%3Fs%20%3Farticle%20%3Fitem%20%3FitemLabel%20WITH%20%7B%0A%20%20SELECT%20DISTINCT%20%3Fs%20%3Farticle%20WHERE%20%7B%0A%20%20%20%20SERVICE%20%3Chttps%3A%2F%2Fdbpedia.org%2Fsparql%3E%20%7B%0A%20%20%20%20%20%20%3Fs%20dbpedia2%3AwikiPageUsesTemplate%20%3Chttp%3A%2F%2Fdbpedia.org%2Fresource%2FTemplate%3AChembox%3E.%0A%20%20%20%20%20%20%3Farticle_db%20foaf%3AprimaryTopic%20%3Fs.%0A%20%20%20%20%7D%0A%20%20%20%20BIND%20%28IRI%28REPLACE%28STR%28%3Farticle_db%29%2C%20%22http%3A%2F%2F%22%2C%20%22https%3A%2F%2F%22%2C%20%22i%22%29%29%20AS%20%3Farticle%29%0A%20%20%7D%0A%7D%20AS%20%25DBPEDIA%20WITH%20%7B%0A%20%20SELECT%20DISTINCT%20%3Fs%20%3Farticle%20%3Fitem%20WHERE%20%7B%0A%20%20%20%20INCLUDE%20%25DBPEDIA%0A%20%20%20%20%3Farticle%20schema%3Aabout%20%3Fitem%20.%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP233%20%5B%5D%20%7D%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP2017%20%5B%5D%20%7D%0A%20%20%20%20MINUS%20%7B%20%3Fitem%20wdt%3AP10718%20%5B%5D%20%7D%0A%20%20%7D%0A%7D%20AS%20%25CHEMICALS%20WHERE%20%7B%0A%20%20INCLUDE%20%25CHEMICALS%0A%20%20VALUES%20%3Fchemicals%20%7B%20wd%3AQ113145171%20wd%3AQ59199015%20%7D%0A%20%20%3Fitem%20wdt%3AP31%20%3Fchemicals.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A)


### Output
<table>
  <tr>
    <td><b>s</b></td>
    <td><b>article</b></td>
    <td><b>item</b></td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Vanadium(V)_chloride_chlorimide</td>
    <td>https://en.wikipedia.org/wiki/Vanadium(V)_chloride_chlorimide</td>
    <td><a href="https://scholia.toolforge.org/Q100341984">vanadium(V) chloride chlorimide</a> (<a href="http://www.wikidata.org/entity/Q100341984">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_tetracarbonyliron_hydride</td>
    <td>https://en.wikipedia.org/wiki/Potassium_tetracarbonyliron_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q100552750">potassium tetracarbonyliron hydride</a> (<a href="http://www.wikidata.org/entity/Q100552750">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/(Triphenylphosphine)iron_tetracarbonyl</td>
    <td>https://en.wikipedia.org/wiki/(Triphenylphosphine)iron_tetracarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q100693702">(triphenylphosphine)iron tetracarbonyl</a> (<a href="http://www.wikidata.org/entity/Q100693702">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bis(triphenylphosphine)iron_tricarbonyl</td>
    <td>https://en.wikipedia.org/wiki/Bis(triphenylphosphine)iron_tricarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q100693878">bis(triphenylphosphine)iron tricarbonyl</a> (<a href="http://www.wikidata.org/entity/Q100693878">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zinc_diphosphide</td>
    <td>https://en.wikipedia.org/wiki/Zinc_diphosphide</td>
    <td><a href="https://scholia.toolforge.org/Q100775201">zinc diphosphide</a> (<a href="http://www.wikidata.org/entity/Q100775201">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lutetium_phthalocyanine</td>
    <td>https://en.wikipedia.org/wiki/Lutetium_phthalocyanine</td>
    <td><a href="https://scholia.toolforge.org/Q104153541">lutetium phthalocyanine</a> (<a href="http://www.wikidata.org/entity/Q104153541">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cobalt_tris(diethyldithiocarbamate)</td>
    <td>https://en.wikipedia.org/wiki/Cobalt_tris(diethyldithiocarbamate)</td>
    <td><a href="https://scholia.toolforge.org/Q104714337">cobalt tris(diethyldithiocarbamate)</a> (<a href="http://www.wikidata.org/entity/Q104714337">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Silicon_carbonate</td>
    <td>https://en.wikipedia.org/wiki/Silicon_carbonate</td>
    <td><a href="https://scholia.toolforge.org/Q104841913">silicon carbonate</a> (<a href="http://www.wikidata.org/entity/Q104841913">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Gallium_monoiodide</td>
    <td>https://en.wikipedia.org/wiki/Gallium_monoiodide</td>
    <td><a href="https://scholia.toolforge.org/Q104858782">gallium monoiodide</a> (<a href="http://www.wikidata.org/entity/Q104858782">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_hypochromate</td>
    <td>https://en.wikipedia.org/wiki/Potassium_hypochromate</td>
    <td><a href="https://scholia.toolforge.org/Q108910775">potassium hypochromate</a> (<a href="http://www.wikidata.org/entity/Q108910775">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Einsteinium(III)_bromide</td>
    <td>https://en.wikipedia.org/wiki/Einsteinium(III)_bromide</td>
    <td><a href="https://scholia.toolforge.org/Q108919658">Einsteinium(III) bromide</a> (<a href="http://www.wikidata.org/entity/Q108919658">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nickel_niobate</td>
    <td>https://en.wikipedia.org/wiki/Nickel_niobate</td>
    <td><a href="https://scholia.toolforge.org/Q109655072">nickel niobate</a> (<a href="http://www.wikidata.org/entity/Q109655072">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Hopeanol</td>
    <td>https://en.wikipedia.org/wiki/Hopeanol</td>
    <td><a href="https://scholia.toolforge.org/Q111165883">Hopeanol</a> (<a href="http://www.wikidata.org/entity/Q111165883">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Copper_naproxen</td>
    <td>https://en.wikipedia.org/wiki/Copper_naproxen</td>
    <td><a href="https://scholia.toolforge.org/Q111661599">copper naproxen</a> (<a href="http://www.wikidata.org/entity/Q111661599">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Blastmycin</td>
    <td>https://en.wikipedia.org/wiki/Blastmycin</td>
    <td><a href="https://scholia.toolforge.org/Q112425399">blastmycin</a> (<a href="http://www.wikidata.org/entity/Q112425399">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Capomycin</td>
    <td>https://en.wikipedia.org/wiki/Capomycin</td>
    <td><a href="https://scholia.toolforge.org/Q112672126">Capomycin</a> (<a href="http://www.wikidata.org/entity/Q112672126">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_enneabromodibismuthate</td>
    <td>https://en.wikipedia.org/wiki/Caesium_enneabromodibismuthate</td>
    <td><a href="https://scholia.toolforge.org/Q112743479">tricesium nonabromodibismuthate</a> (<a href="http://www.wikidata.org/entity/Q112743479">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_tritelluride</td>
    <td>https://en.wikipedia.org/wiki/Lithium_tritelluride</td>
    <td><a href="https://scholia.toolforge.org/Q113130309">lithium tritelluride</a> (<a href="http://www.wikidata.org/entity/Q113130309">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Holmium_acetylacetonate</td>
    <td>https://en.wikipedia.org/wiki/Holmium_acetylacetonate</td>
    <td><a href="https://scholia.toolforge.org/Q113137820">Holmium acetylacetonate</a> (<a href="http://www.wikidata.org/entity/Q113137820">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Praseodymium(V)_oxide_nitride</td>
    <td>https://en.wikipedia.org/wiki/Praseodymium(V)_oxide_nitride</td>
    <td><a href="https://scholia.toolforge.org/Q113142445">Praseodymium(V) oxide nitride</a> (<a href="http://www.wikidata.org/entity/Q113142445">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Praseodymium_orthoscandate</td>
    <td>https://en.wikipedia.org/wiki/Praseodymium_orthoscandate</td>
    <td><a href="https://scholia.toolforge.org/Q113157151">Praseodymium orthoscandate</a> (<a href="http://www.wikidata.org/entity/Q113157151">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Trisodium_pentaborate</td>
    <td>https://en.wikipedia.org/wiki/Trisodium_pentaborate</td>
    <td><a href="https://scholia.toolforge.org/Q113371966">Trisodium pentaborate</a> (<a href="http://www.wikidata.org/entity/Q113371966">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Hafnium_carbonitride</td>
    <td>https://en.wikipedia.org/wiki/Hafnium_carbonitride</td>
    <td><a href="https://scholia.toolforge.org/Q113514900">hafnium carbonitride</a> (<a href="http://www.wikidata.org/entity/Q113514900">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Globo_H</td>
    <td>https://en.wikipedia.org/wiki/Globo_H</td>
    <td><a href="https://scholia.toolforge.org/Q105973358">Globo H</a> (<a href="http://www.wikidata.org/entity/Q105973358">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Dysprosium_stannate</td>
    <td>https://en.wikipedia.org/wiki/Dysprosium_stannate</td>
    <td><a href="https://scholia.toolforge.org/Q106196296">dysprosium stannate</a> (<a href="http://www.wikidata.org/entity/Q106196296">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Copper_oxide_selenite</td>
    <td>https://en.wikipedia.org/wiki/Copper_oxide_selenite</td>
    <td><a href="https://scholia.toolforge.org/Q106435354">copper oxide selenite</a> (<a href="http://www.wikidata.org/entity/Q106435354">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Trichromium_silicide</td>
    <td>https://en.wikipedia.org/wiki/Trichromium_silicide</td>
    <td><a href="https://scholia.toolforge.org/Q106616219">Trichromium silicide</a> (<a href="http://www.wikidata.org/entity/Q106616219">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Chromium(IV)_silicide</td>
    <td>https://en.wikipedia.org/wiki/Chromium(IV)_silicide</td>
    <td><a href="https://scholia.toolforge.org/Q106616247">Chromium(IV) silicide</a> (<a href="http://www.wikidata.org/entity/Q106616247">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Rubidium_sesquioxide</td>
    <td>https://en.wikipedia.org/wiki/Rubidium_sesquioxide</td>
    <td><a href="https://scholia.toolforge.org/Q108101923">Rubidium sesquioxide</a> (<a href="http://www.wikidata.org/entity/Q108101923">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Europium(III)_chromate</td>
    <td>https://en.wikipedia.org/wiki/Europium(III)_chromate</td>
    <td><a href="https://scholia.toolforge.org/Q108486519">Europium chromate</a> (<a href="http://www.wikidata.org/entity/Q108486519">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Yttrium(II)_oxide</td>
    <td>https://en.wikipedia.org/wiki/Yttrium(II)_oxide</td>
    <td><a href="https://scholia.toolforge.org/Q108503358">yttrium(II) oxide</a> (<a href="http://www.wikidata.org/entity/Q108503358">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Scandium_phosphide</td>
    <td>https://en.wikipedia.org/wiki/Scandium_phosphide</td>
    <td><a href="https://scholia.toolforge.org/Q110050616">scandium phosphide</a> (<a href="http://www.wikidata.org/entity/Q110050616">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Terbium_phosphide</td>
    <td>https://en.wikipedia.org/wiki/Terbium_phosphide</td>
    <td><a href="https://scholia.toolforge.org/Q110248455">terbium phosphide</a> (<a href="http://www.wikidata.org/entity/Q110248455">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Gadolinium_phosphide</td>
    <td>https://en.wikipedia.org/wiki/Gadolinium_phosphide</td>
    <td><a href="https://scholia.toolforge.org/Q110248530">gadolinium phosphide</a> (<a href="http://www.wikidata.org/entity/Q110248530">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Holmium_phosphide</td>
    <td>https://en.wikipedia.org/wiki/Holmium_phosphide</td>
    <td><a href="https://scholia.toolforge.org/Q110253864">holmium phosphide</a> (<a href="http://www.wikidata.org/entity/Q110253864">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Francium_chloride</td>
    <td>https://en.wikipedia.org/wiki/Francium_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q110852929">francium chloride</a> (<a href="http://www.wikidata.org/entity/Q110852929">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tantalum_arsenide</td>
    <td>https://en.wikipedia.org/wiki/Tantalum_arsenide</td>
    <td><a href="https://scholia.toolforge.org/Q115409212">tantalum arsenide</a> (<a href="http://www.wikidata.org/entity/Q115409212">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Europium_barium_titanate</td>
    <td>https://en.wikipedia.org/wiki/Europium_barium_titanate</td>
    <td><a href="https://scholia.toolforge.org/Q131540324">barium europium(II) dititanium(IV) oxide</a> (<a href="http://www.wikidata.org/entity/Q131540324">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Ribulose</td>
    <td>https://en.wikipedia.org/wiki/Ribulose</td>
    <td><a href="https://scholia.toolforge.org/Q57830363">ribulose</a> (<a href="http://www.wikidata.org/entity/Q57830363">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Ruthenium(III)_acetate</td>
    <td>https://en.wikipedia.org/wiki/Ruthenium(III)_acetate</td>
    <td><a href="https://scholia.toolforge.org/Q59197074">ruthenium(III) acetate</a> (<a href="http://www.wikidata.org/entity/Q59197074">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/(Pentamethylcyclopentadienyl)aluminium(I)</td>
    <td>https://en.wikipedia.org/wiki/(Pentamethylcyclopentadienyl)aluminium(I)</td>
    <td><a href="https://scholia.toolforge.org/Q59284842">(pentamethylcyclopentadienyl)aluminium(I)</a> (<a href="http://www.wikidata.org/entity/Q59284842">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iridium_disulfide</td>
    <td>https://en.wikipedia.org/wiki/Iridium_disulfide</td>
    <td><a href="https://scholia.toolforge.org/Q60723865">iridium disulfide</a> (<a href="http://www.wikidata.org/entity/Q60723865">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Prymnesin-B1</td>
    <td>https://en.wikipedia.org/wiki/Prymnesin-B1</td>
    <td><a href="https://scholia.toolforge.org/Q70881796">prymnesin-B1</a> (<a href="http://www.wikidata.org/entity/Q70881796">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cyclooctadiene_iridium_methoxide_dimer</td>
    <td>https://en.wikipedia.org/wiki/Cyclooctadiene_iridium_methoxide_dimer</td>
    <td><a href="https://scholia.toolforge.org/Q72444802">bis(1,5-cyclooctadiene)dimethoxydiiridium</a> (<a href="http://www.wikidata.org/entity/Q72444802">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bismuth(III)_acetate</td>
    <td>https://en.wikipedia.org/wiki/Bismuth(III)_acetate</td>
    <td><a href="https://scholia.toolforge.org/Q72446531">Bismuth acetate</a> (<a href="http://www.wikidata.org/entity/Q72446531">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Decamethylzirconocene_dichloride</td>
    <td>https://en.wikipedia.org/wiki/Decamethylzirconocene_dichloride</td>
    <td><a href="https://scholia.toolforge.org/Q72446706">bis(pentamethylcyclopentadienyl)zirconium dichloride</a> (<a href="http://www.wikidata.org/entity/Q72446706">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/(Cyclooctatetraene)iron_tricarbonyl</td>
    <td>https://en.wikipedia.org/wiki/(Cyclooctatetraene)iron_tricarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q72460225">cyclooctatetraenetricarbonyliron</a> (<a href="http://www.wikidata.org/entity/Q72460225">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tricarbonylchloroglycinatoruthenium(II)</td>
    <td>https://en.wikipedia.org/wiki/Tricarbonylchloroglycinatoruthenium(II)</td>
    <td><a href="https://scholia.toolforge.org/Q72510167">(OC-6-44)-Tricarbonylchloro(glycinato)ruthenium</a> (<a href="http://www.wikidata.org/entity/Q72510167">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/C12-15_pareth-12</td>
    <td>https://en.wikipedia.org/wiki/C12-15_pareth-12</td>
    <td><a href="https://scholia.toolforge.org/Q96374179">C12-15 pareth-12</a> (<a href="http://www.wikidata.org/entity/Q96374179">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_disilicate</td>
    <td>https://en.wikipedia.org/wiki/Lithium_disilicate</td>
    <td><a href="https://scholia.toolforge.org/Q96390498">Lithium disilicate</a> (<a href="http://www.wikidata.org/entity/Q96390498">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Aluminium_monohydroxide</td>
    <td>https://en.wikipedia.org/wiki/Aluminium_monohydroxide</td>
    <td><a href="https://scholia.toolforge.org/Q97163408">hydroxyaluminium(I)</a> (<a href="http://www.wikidata.org/entity/Q97163408">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Das_cubane</td>
    <td>https://en.wikipedia.org/wiki/Das_cubane</td>
    <td><a href="https://scholia.toolforge.org/Q97357582">Das cubane</a> (<a href="http://www.wikidata.org/entity/Q97357582">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iron(tetraphenylporphyrinato)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Iron(tetraphenylporphyrinato)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q97358990">Iron(tetraphenylporphyrinato) chloride</a> (<a href="http://www.wikidata.org/entity/Q97358990">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Americium(III)_hydroxide</td>
    <td>https://en.wikipedia.org/wiki/Americium(III)_hydroxide</td>
    <td><a href="https://scholia.toolforge.org/Q97359030">Americium(III) hydroxide</a> (<a href="http://www.wikidata.org/entity/Q97359030">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cis-Dichlorobis(bipyridine)ruthenium(II)</td>
    <td>https://en.wikipedia.org/wiki/Cis-Dichlorobis(bipyridine)ruthenium(II)</td>
    <td><a href="https://scholia.toolforge.org/Q97359792">Cis-Dichlorobis(bipyridine)ruthenium(II)</a> (<a href="http://www.wikidata.org/entity/Q97359792">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iron_germanide</td>
    <td>https://en.wikipedia.org/wiki/Iron_germanide</td>
    <td><a href="https://scholia.toolforge.org/Q97933197">Iron germanide</a> (<a href="http://www.wikidata.org/entity/Q97933197">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Manganese_germanide</td>
    <td>https://en.wikipedia.org/wiki/Manganese_germanide</td>
    <td><a href="https://scholia.toolforge.org/Q97933222">Manganese germanide</a> (<a href="http://www.wikidata.org/entity/Q97933222">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_octacyanomolybdate(IV)</td>
    <td>https://en.wikipedia.org/wiki/Potassium_octacyanomolybdate(IV)</td>
    <td><a href="https://scholia.toolforge.org/Q98078085">Potassium octacyanomolybdate(IV)</a> (<a href="http://www.wikidata.org/entity/Q98078085">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Fosetyl-Al</td>
    <td>https://en.wikipedia.org/wiki/Fosetyl-Al</td>
    <td><a href="https://scholia.toolforge.org/Q56063007">Fosetyl-Al</a> (<a href="http://www.wikidata.org/entity/Q56063007">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Thorium_monoxide</td>
    <td>https://en.wikipedia.org/wiki/Thorium_monoxide</td>
    <td><a href="https://scholia.toolforge.org/Q56119851">thorium monoxide</a> (<a href="http://www.wikidata.org/entity/Q56119851">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Basic_lead_phosphite</td>
    <td>https://en.wikipedia.org/wiki/Basic_lead_phosphite</td>
    <td><a href="https://scholia.toolforge.org/Q56291559">basic lead phosphite</a> (<a href="http://www.wikidata.org/entity/Q56291559">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Vinylferrocene</td>
    <td>https://en.wikipedia.org/wiki/Vinylferrocene</td>
    <td><a href="https://scholia.toolforge.org/Q56291686">Vinylferrocene</a> (<a href="http://www.wikidata.org/entity/Q56291686">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bis(triphenylphosphine)rhodium_carbonyl_chloride</td>
    <td>https://en.wikipedia.org/wiki/Bis(triphenylphosphine)rhodium_carbonyl_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q56291871">Bis(triphenylphosphine)rhodium carbonyl chloride</a> (<a href="http://www.wikidata.org/entity/Q56291871">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Hexaphenylcarbodiphosphorane</td>
    <td>https://en.wikipedia.org/wiki/Hexaphenylcarbodiphosphorane</td>
    <td><a href="https://scholia.toolforge.org/Q56291924">Hexaphenylcarbodiphosphorane</a> (<a href="http://www.wikidata.org/entity/Q56291924">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Vanadium(III)_acetylacetonate</td>
    <td>https://en.wikipedia.org/wiki/Vanadium(III)_acetylacetonate</td>
    <td><a href="https://scholia.toolforge.org/Q56605537">vanadium(III) acetylacetonate</a> (<a href="http://www.wikidata.org/entity/Q56605537">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Silicalite</td>
    <td>https://en.wikipedia.org/wiki/Silicalite</td>
    <td><a href="https://scholia.toolforge.org/Q56811200">silicalite</a> (<a href="http://www.wikidata.org/entity/Q56811200">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/(Cyclopentadienyl)zirconium_trichloride</td>
    <td>https://en.wikipedia.org/wiki/(Cyclopentadienyl)zirconium_trichloride</td>
    <td><a href="https://scholia.toolforge.org/Q61818999">(cyclopentadienyl)zirconium trichloride</a> (<a href="http://www.wikidata.org/entity/Q61818999">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Ferrioxalate</td>
    <td>https://en.wikipedia.org/wiki/Ferrioxalate</td>
    <td><a href="https://scholia.toolforge.org/Q62578925">ferrioxalate</a> (<a href="http://www.wikidata.org/entity/Q62578925">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Thulium(II)_fluoride</td>
    <td>https://en.wikipedia.org/wiki/Thulium(II)_fluoride</td>
    <td><a href="https://scholia.toolforge.org/Q65051115">thulium difluoride</a> (<a href="http://www.wikidata.org/entity/Q65051115">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cyclopentadienyl_magnesium_bromide</td>
    <td>https://en.wikipedia.org/wiki/Cyclopentadienyl_magnesium_bromide</td>
    <td><a href="https://scholia.toolforge.org/Q65062358">Cyclopentadienyl magnesium bromide</a> (<a href="http://www.wikidata.org/entity/Q65062358">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bilirubin_glucuronide</td>
    <td>https://en.wikipedia.org/wiki/Bilirubin_glucuronide</td>
    <td><a href="https://scholia.toolforge.org/Q65067489">Bilirubin glucuronide</a> (<a href="http://www.wikidata.org/entity/Q65067489">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Hexaammineplatinum(IV)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Hexaammineplatinum(IV)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q65071755">Hexaammineplatinum(IV) chloride</a> (<a href="http://www.wikidata.org/entity/Q65071755">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Boron_monohydride</td>
    <td>https://en.wikipedia.org/wiki/Boron_monohydride</td>
    <td><a href="https://scholia.toolforge.org/Q66087945">boron monohydride</a> (<a href="http://www.wikidata.org/entity/Q66087945">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Francium_hydroxide</td>
    <td>https://en.wikipedia.org/wiki/Francium_hydroxide</td>
    <td><a href="https://scholia.toolforge.org/Q68102359">francium hydroxide</a> (<a href="http://www.wikidata.org/entity/Q68102359">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Copper(II)_cyanurate</td>
    <td>https://en.wikipedia.org/wiki/Copper(II)_cyanurate</td>
    <td><a href="https://scholia.toolforge.org/Q85754040">Copper(II) cyanurate</a> (<a href="http://www.wikidata.org/entity/Q85754040">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/N,N-Dimethylaminomethylferrocene</td>
    <td>https://en.wikipedia.org/wiki/N,N-Dimethylaminomethylferrocene</td>
    <td><a href="https://scholia.toolforge.org/Q89986085">N,N-Dimethylaminomethylferrocene</a> (<a href="http://www.wikidata.org/entity/Q89986085">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Triphosphorus_pentanitride</td>
    <td>https://en.wikipedia.org/wiki/Triphosphorus_pentanitride</td>
    <td><a href="https://scholia.toolforge.org/Q15427074">triphosphorus pentanitride</a> (<a href="http://www.wikidata.org/entity/Q15427074">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Ammonium_dimolybdate</td>
    <td>https://en.wikipedia.org/wiki/Ammonium_dimolybdate</td>
    <td><a href="https://scholia.toolforge.org/Q20658352">Ammonium dimolybdate</a> (<a href="http://www.wikidata.org/entity/Q20658352">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Rhodium_carbonyl_chloride</td>
    <td>https://en.wikipedia.org/wiki/Rhodium_carbonyl_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q20671903">rhodium carbonyl chloride</a> (<a href="http://www.wikidata.org/entity/Q20671903">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Calcium_polonide</td>
    <td>https://en.wikipedia.org/wiki/Calcium_polonide</td>
    <td><a href="https://scholia.toolforge.org/Q20984966">calcium polonide</a> (<a href="http://www.wikidata.org/entity/Q20984966">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tantalum(V)_iodide</td>
    <td>https://en.wikipedia.org/wiki/Tantalum(V)_iodide</td>
    <td><a href="https://scholia.toolforge.org/Q21079499">tantalum pentaiodide dimer</a> (<a href="http://www.wikidata.org/entity/Q21079499">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tetramethyl_acetyloctahydronaphthalenes</td>
    <td>https://en.wikipedia.org/wiki/Tetramethyl_acetyloctahydronaphthalenes</td>
    <td><a href="https://scholia.toolforge.org/Q21099589">tetramethyl acetyloctahydronaphthalenes</a> (<a href="http://www.wikidata.org/entity/Q21099589">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Atrop-abyssomicin_C</td>
    <td>https://en.wikipedia.org/wiki/Atrop-abyssomicin_C</td>
    <td><a href="https://scholia.toolforge.org/Q21099609">Atrop-abyssomicin C</a> (<a href="http://www.wikidata.org/entity/Q21099609">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Trimethyldiborane</td>
    <td>https://en.wikipedia.org/wiki/Trimethyldiborane</td>
    <td><a href="https://scholia.toolforge.org/Q21099644">trimethyldiborane</a> (<a href="http://www.wikidata.org/entity/Q21099644">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Uroerythrin</td>
    <td>https://en.wikipedia.org/wiki/Uroerythrin</td>
    <td><a href="https://scholia.toolforge.org/Q22255716">Uroerythrin</a> (<a href="http://www.wikidata.org/entity/Q22255716">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Rhodium-platinum_oxide</td>
    <td>https://en.wikipedia.org/wiki/Rhodium-platinum_oxide</td>
    <td><a href="https://scholia.toolforge.org/Q22908317">Rhodium-platinum oxide</a> (<a href="http://www.wikidata.org/entity/Q22908317">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cobalt(II)_phosphide</td>
    <td>https://en.wikipedia.org/wiki/Cobalt(II)_phosphide</td>
    <td><a href="https://scholia.toolforge.org/Q27695609">Cobalt(II) phosphide</a> (<a href="http://www.wikidata.org/entity/Q27695609">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cycloheptatrienemolybdenum_tricarbonyl</td>
    <td>https://en.wikipedia.org/wiki/Cycloheptatrienemolybdenum_tricarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q27983661">cycloheptatrienemolybdenum tricarbonyl</a> (<a href="http://www.wikidata.org/entity/Q27983661">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tris(4-bromophenyl)ammoniumyl_hexachloroantimonate</td>
    <td>https://en.wikipedia.org/wiki/Tris(4-bromophenyl)ammoniumyl_hexachloroantimonate</td>
    <td><a href="https://scholia.toolforge.org/Q28457710">tris(4-bromophenyl)ammoniumyl hexachloroantimonate</a> (<a href="http://www.wikidata.org/entity/Q28457710">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bismuth_phosphide</td>
    <td>https://en.wikipedia.org/wiki/Bismuth_phosphide</td>
    <td><a href="https://scholia.toolforge.org/Q28790590">bismuth phosphide</a> (<a href="http://www.wikidata.org/entity/Q28790590">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iron(II)_selenate</td>
    <td>https://en.wikipedia.org/wiki/Iron(II)_selenate</td>
    <td><a href="https://scholia.toolforge.org/Q30020425">Iron(II) selenate</a> (<a href="http://www.wikidata.org/entity/Q30020425">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nitrogen_pentahydride</td>
    <td>https://en.wikipedia.org/wiki/Nitrogen_pentahydride</td>
    <td><a href="https://scholia.toolforge.org/Q37497367">nitrogen pentahydride</a> (<a href="http://www.wikidata.org/entity/Q37497367">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_hexafluorogermanate</td>
    <td>https://en.wikipedia.org/wiki/Lithium_hexafluorogermanate</td>
    <td><a href="https://scholia.toolforge.org/Q40889202">Lithium hexafluorogermanate</a> (<a href="http://www.wikidata.org/entity/Q40889202">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nickel_bis(dimethyldithiocarbamate)</td>
    <td>https://en.wikipedia.org/wiki/Nickel_bis(dimethyldithiocarbamate)</td>
    <td><a href="https://scholia.toolforge.org/Q48791498">Nickel bis(dimethyldithiocarbamate)</a> (<a href="http://www.wikidata.org/entity/Q48791498">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iridium(III)_sulfide</td>
    <td>https://en.wikipedia.org/wiki/Iridium(III)_sulfide</td>
    <td><a href="https://scholia.toolforge.org/Q48796552">iridium(III) sulfide</a> (<a href="http://www.wikidata.org/entity/Q48796552">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Sirohydrochlorin</td>
    <td>https://en.wikipedia.org/wiki/Sirohydrochlorin</td>
    <td><a href="https://scholia.toolforge.org/Q48838605">Sirohydrochlorin</a> (<a href="http://www.wikidata.org/entity/Q48838605">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Promethium(III)_nitrate</td>
    <td>https://en.wikipedia.org/wiki/Promethium(III)_nitrate</td>
    <td><a href="https://scholia.toolforge.org/Q48937859">promethium(III) nitrate</a> (<a href="http://www.wikidata.org/entity/Q48937859">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Promethium(III)_hydroxide</td>
    <td>https://en.wikipedia.org/wiki/Promethium(III)_hydroxide</td>
    <td><a href="https://scholia.toolforge.org/Q48937875">Promethium hydroxide</a> (<a href="http://www.wikidata.org/entity/Q48937875">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Europium_hydride</td>
    <td>https://en.wikipedia.org/wiki/Europium_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q48937885">europium(II) hydride</a> (<a href="http://www.wikidata.org/entity/Q48937885">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Telluropyrylium</td>
    <td>https://en.wikipedia.org/wiki/Telluropyrylium</td>
    <td><a href="https://scholia.toolforge.org/Q48996169">telluropyrylium</a> (<a href="http://www.wikidata.org/entity/Q48996169">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lutetium_vanadate</td>
    <td>https://en.wikipedia.org/wiki/Lutetium_vanadate</td>
    <td><a href="https://scholia.toolforge.org/Q49748121">lutetium vanadate</a> (<a href="http://www.wikidata.org/entity/Q49748121">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Deoxyadenosyl_radical</td>
    <td>https://en.wikipedia.org/wiki/Deoxyadenosyl_radical</td>
    <td><a href="https://scholia.toolforge.org/Q55080209">Deoxyadenosyl radical</a> (<a href="http://www.wikidata.org/entity/Q55080209">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/(Butadiene)iron_tricarbonyl</td>
    <td>https://en.wikipedia.org/wiki/(Butadiene)iron_tricarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q55086423">(butadiene)iron tricarbonyl</a> (<a href="http://www.wikidata.org/entity/Q55086423">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Ferrichrome_A</td>
    <td>https://en.wikipedia.org/wiki/Ferrichrome_A</td>
    <td><a href="https://scholia.toolforge.org/Q55286742">Ferrichrome A</a> (<a href="http://www.wikidata.org/entity/Q55286742">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Praseodymium_arsenate</td>
    <td>https://en.wikipedia.org/wiki/Praseodymium_arsenate</td>
    <td><a href="https://scholia.toolforge.org/Q55581001">praseodymium(III) arsonate</a> (<a href="http://www.wikidata.org/entity/Q55581001">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Europium(III)_arsenate</td>
    <td>https://en.wikipedia.org/wiki/Europium(III)_arsenate</td>
    <td><a href="https://scholia.toolforge.org/Q55581092">europium(III) arsenate</a> (<a href="http://www.wikidata.org/entity/Q55581092">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Carbomethoxymethylenetriphenylphosphorane</td>
    <td>https://en.wikipedia.org/wiki/Carbomethoxymethylenetriphenylphosphorane</td>
    <td><a href="https://scholia.toolforge.org/Q55606637">carbomethoxymethylenetriphenylphosphorane</a> (<a href="http://www.wikidata.org/entity/Q55606637">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cembratrienol</td>
    <td>https://en.wikipedia.org/wiki/Cembratrienol</td>
    <td><a href="https://scholia.toolforge.org/Q55606816">cembratrienol</a> (<a href="http://www.wikidata.org/entity/Q55606816">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Pentamethylmolybdenum</td>
    <td>https://en.wikipedia.org/wiki/Pentamethylmolybdenum</td>
    <td><a href="https://scholia.toolforge.org/Q55629455">Pentamethylmolybdenum</a> (<a href="http://www.wikidata.org/entity/Q55629455">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Niobium_diboride</td>
    <td>https://en.wikipedia.org/wiki/Niobium_diboride</td>
    <td><a href="https://scholia.toolforge.org/Q55641268">Niobium diboride</a> (<a href="http://www.wikidata.org/entity/Q55641268">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bis(cyclooctatetraene)iron</td>
    <td>https://en.wikipedia.org/wiki/Bis(cyclooctatetraene)iron</td>
    <td><a href="https://scholia.toolforge.org/Q18378643">bis(cyclooctatetraene)iron</a> (<a href="http://www.wikidata.org/entity/Q18378643">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cobalt_boride</td>
    <td>https://en.wikipedia.org/wiki/Cobalt_boride</td>
    <td><a href="https://scholia.toolforge.org/Q18391581">cobalt boride</a> (<a href="http://www.wikidata.org/entity/Q18391581">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Americium(II)_bromide</td>
    <td>https://en.wikipedia.org/wiki/Americium(II)_bromide</td>
    <td><a href="https://scholia.toolforge.org/Q19595872">americium(II) bromide</a> (<a href="http://www.wikidata.org/entity/Q19595872">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Americium(II)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Americium(II)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q19595873">americium(II) chloride</a> (<a href="http://www.wikidata.org/entity/Q19595873">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Americium(II)_iodide</td>
    <td>https://en.wikipedia.org/wiki/Americium(II)_iodide</td>
    <td><a href="https://scholia.toolforge.org/Q19595874">americium(II) iodide</a> (<a href="http://www.wikidata.org/entity/Q19595874">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Titanium_perchlorate</td>
    <td>https://en.wikipedia.org/wiki/Titanium_perchlorate</td>
    <td><a href="https://scholia.toolforge.org/Q24836734">titanium perchlorate</a> (<a href="http://www.wikidata.org/entity/Q24836734">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tetramethylammonium_auride</td>
    <td>https://en.wikipedia.org/wiki/Tetramethylammonium_auride</td>
    <td><a href="https://scholia.toolforge.org/Q24836885">tetramethylammonium auride</a> (<a href="http://www.wikidata.org/entity/Q24836885">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bismuth_titanate</td>
    <td>https://en.wikipedia.org/wiki/Bismuth_titanate</td>
    <td><a href="https://scholia.toolforge.org/Q25055622">bismuth titanate</a> (<a href="http://www.wikidata.org/entity/Q25055622">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/14-Methoxydihydromorphinone</td>
    <td>https://en.wikipedia.org/wiki/14-Methoxydihydromorphinone</td>
    <td><a href="https://scholia.toolforge.org/Q25099572">14-methoxydihydromorphinone</a> (<a href="http://www.wikidata.org/entity/Q25099572">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/PEG-PVA</td>
    <td>https://en.wikipedia.org/wiki/PEG-PVA</td>
    <td><a href="https://scholia.toolforge.org/Q25101580">PEG-PVA</a> (<a href="http://www.wikidata.org/entity/Q25101580">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bismuth_antimonide</td>
    <td>https://en.wikipedia.org/wiki/Bismuth_antimonide</td>
    <td><a href="https://scholia.toolforge.org/Q25304545">bismuth antimonide</a> (<a href="http://www.wikidata.org/entity/Q25304545">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Borane_tert-butylamine</td>
    <td>https://en.wikipedia.org/wiki/Borane_tert-butylamine</td>
    <td><a href="https://scholia.toolforge.org/Q25323688">borane tert-butylamine complex</a> (<a href="http://www.wikidata.org/entity/Q25323688">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Ruthenium_pentacarbonyl</td>
    <td>https://en.wikipedia.org/wiki/Ruthenium_pentacarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q25323976">ruthenium pentacarbonyl</a> (<a href="http://www.wikidata.org/entity/Q25323976">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Gephyronic_acid</td>
    <td>https://en.wikipedia.org/wiki/Gephyronic_acid</td>
    <td><a href="https://scholia.toolforge.org/Q25323989">Gephyronic acid</a> (<a href="http://www.wikidata.org/entity/Q25323989">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tetrakis(cyclopentadienyl)uranium(IV)</td>
    <td>https://en.wikipedia.org/wiki/Tetrakis(cyclopentadienyl)uranium(IV)</td>
    <td><a href="https://scholia.toolforge.org/Q25351930">Tetrakis(cyclopentadienyl)uranium(IV)</a> (<a href="http://www.wikidata.org/entity/Q25351930">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_ruthenate</td>
    <td>https://en.wikipedia.org/wiki/Lithium_ruthenate</td>
    <td><a href="https://scholia.toolforge.org/Q30577742">Lithium ruthenate</a> (<a href="http://www.wikidata.org/entity/Q30577742">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zirconium_perchlorate</td>
    <td>https://en.wikipedia.org/wiki/Zirconium_perchlorate</td>
    <td><a href="https://scholia.toolforge.org/Q30588324">zirconium perchlorate</a> (<a href="http://www.wikidata.org/entity/Q30588324">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_iridate</td>
    <td>https://en.wikipedia.org/wiki/Lithium_iridate</td>
    <td><a href="https://scholia.toolforge.org/Q30595424">lithium iridate</a> (<a href="http://www.wikidata.org/entity/Q30595424">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_platinate</td>
    <td>https://en.wikipedia.org/wiki/Lithium_platinate</td>
    <td><a href="https://scholia.toolforge.org/Q30595428">lithium platinate</a> (<a href="http://www.wikidata.org/entity/Q30595428">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bis(cyclopentadienyl)titanium(III)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Bis(cyclopentadienyl)titanium(III)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q30605305">Bis(cyclopentadienyl)titanium(III) chloride</a> (<a href="http://www.wikidata.org/entity/Q30605305">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Pentakis(dimethylamido)tantalum</td>
    <td>https://en.wikipedia.org/wiki/Pentakis(dimethylamido)tantalum</td>
    <td><a href="https://scholia.toolforge.org/Q30607953">Pentakis(dimethylamino)tantalum(V)</a> (<a href="http://www.wikidata.org/entity/Q30607953">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Pentamethylcyclopentadienyl_rhodium_dichloride_dimer</td>
    <td>https://en.wikipedia.org/wiki/Pentamethylcyclopentadienyl_rhodium_dichloride_dimer</td>
    <td><a href="https://scholia.toolforge.org/Q30682572">pentamethylcyclopentadienyl rhodium dichloride dimer</a> (<a href="http://www.wikidata.org/entity/Q30682572">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Monosodium_xenate</td>
    <td>https://en.wikipedia.org/wiki/Monosodium_xenate</td>
    <td><a href="https://scholia.toolforge.org/Q30688950">monosodium xenate</a> (<a href="http://www.wikidata.org/entity/Q30688950">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Pentamethylbismuth</td>
    <td>https://en.wikipedia.org/wiki/Pentamethylbismuth</td>
    <td><a href="https://scholia.toolforge.org/Q30694207">Pentamethylbismuth</a> (<a href="http://www.wikidata.org/entity/Q30694207">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_tetrachloridocuprate(II)</td>
    <td>https://en.wikipedia.org/wiki/Potassium_tetrachloridocuprate(II)</td>
    <td><a href="https://scholia.toolforge.org/Q30716910">potassium tetrachloridocuprate(II)</a> (<a href="http://www.wikidata.org/entity/Q30716910">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nickel_bis(dimethylglyoximate)</td>
    <td>https://en.wikipedia.org/wiki/Nickel_bis(dimethylglyoximate)</td>
    <td><a href="https://scholia.toolforge.org/Q55648446">Nickel bis(dimethylglyoximate)</a> (<a href="http://www.wikidata.org/entity/Q55648446">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Actinium(III)_nitrate</td>
    <td>https://en.wikipedia.org/wiki/Actinium(III)_nitrate</td>
    <td><a href="https://scholia.toolforge.org/Q4321577">actinium(III) nitrate</a> (<a href="http://www.wikidata.org/entity/Q4321577">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Rubidium_ozonide</td>
    <td>https://en.wikipedia.org/wiki/Rubidium_ozonide</td>
    <td><a href="https://scholia.toolforge.org/Q4332243">rubidium ozonide</a> (<a href="http://www.wikidata.org/entity/Q4332243">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Yttrium_oxyfluoride</td>
    <td>https://en.wikipedia.org/wiki/Yttrium_oxyfluoride</td>
    <td><a href="https://scholia.toolforge.org/Q4332915">yttrium oxyfluoride</a> (<a href="http://www.wikidata.org/entity/Q4332915">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Actinium(III)_phosphate</td>
    <td>https://en.wikipedia.org/wiki/Actinium(III)_phosphate</td>
    <td><a href="https://scholia.toolforge.org/Q4337162">actinium(III) orthophosphate</a> (<a href="http://www.wikidata.org/entity/Q4337162">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Rubidium_peroxide</td>
    <td>https://en.wikipedia.org/wiki/Rubidium_peroxide</td>
    <td><a href="https://scholia.toolforge.org/Q4351683">rubidium peroxide</a> (<a href="http://www.wikidata.org/entity/Q4351683">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_peroxide</td>
    <td>https://en.wikipedia.org/wiki/Caesium_peroxide</td>
    <td><a href="https://scholia.toolforge.org/Q4351685">cesium peroxide</a> (<a href="http://www.wikidata.org/entity/Q4351685">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cobalt_monosilicide</td>
    <td>https://en.wikipedia.org/wiki/Cobalt_monosilicide</td>
    <td><a href="https://scholia.toolforge.org/Q4419233">cobalt monosilicide</a> (<a href="http://www.wikidata.org/entity/Q4419233">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Manganese_monosilicide</td>
    <td>https://en.wikipedia.org/wiki/Manganese_monosilicide</td>
    <td><a href="https://scholia.toolforge.org/Q4419236">manganese monosilicide</a> (<a href="http://www.wikidata.org/entity/Q4419236">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Titanium(III)_sulfide</td>
    <td>https://en.wikipedia.org/wiki/Titanium(III)_sulfide</td>
    <td><a href="https://scholia.toolforge.org/Q4445883">titanium sulfide</a> (<a href="http://www.wikidata.org/entity/Q4445883">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nitratoauric_acid</td>
    <td>https://en.wikipedia.org/wiki/Nitratoauric_acid</td>
    <td><a href="https://scholia.toolforge.org/Q4456639">gold(III) hydrogen nitrate</a> (<a href="http://www.wikidata.org/entity/Q4456639">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Ferrovanadium</td>
    <td>https://en.wikipedia.org/wiki/Ferrovanadium</td>
    <td><a href="https://scholia.toolforge.org/Q4483127">ferrovanadium</a> (<a href="http://www.wikidata.org/entity/Q4483127">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Protactinium(V)_fluoride</td>
    <td>https://en.wikipedia.org/wiki/Protactinium(V)_fluoride</td>
    <td><a href="https://scholia.toolforge.org/Q4493226">protactinium(V) fluoride</a> (<a href="http://www.wikidata.org/entity/Q4493226">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tungsten(II)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Tungsten(II)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q4498197">tungsten(II) chloride</a> (<a href="http://www.wikidata.org/entity/Q4498197">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Acetylferrocene</td>
    <td>https://en.wikipedia.org/wiki/Acetylferrocene</td>
    <td><a href="https://scholia.toolforge.org/Q4673312">acetylferrocene</a> (<a href="http://www.wikidata.org/entity/Q4673312">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Adenosine_thiamine_diphosphate</td>
    <td>https://en.wikipedia.org/wiki/Adenosine_thiamine_diphosphate</td>
    <td><a href="https://scholia.toolforge.org/Q4682284">Adenosine thiamine diphosphate</a> (<a href="http://www.wikidata.org/entity/Q4682284">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Aluminium_gallium_indium_phosphide</td>
    <td>https://en.wikipedia.org/wiki/Aluminium_gallium_indium_phosphide</td>
    <td><a href="https://scholia.toolforge.org/Q4737385">Aluminium gallium indium phosphide</a> (<a href="http://www.wikidata.org/entity/Q4737385">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Amavadin</td>
    <td>https://en.wikipedia.org/wiki/Amavadin</td>
    <td><a href="https://scholia.toolforge.org/Q4740693">amavadin</a> (<a href="http://www.wikidata.org/entity/Q4740693">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Glyceryl_hydroxystearate</td>
    <td>https://en.wikipedia.org/wiki/Glyceryl_hydroxystearate</td>
    <td><a href="https://scholia.toolforge.org/Q5572569">glyceryl hydroxystearate</a> (<a href="http://www.wikidata.org/entity/Q5572569">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Glycine_propionyl-L-carnitine</td>
    <td>https://en.wikipedia.org/wiki/Glycine_propionyl-L-carnitine</td>
    <td><a href="https://scholia.toolforge.org/Q5572581">Glycine propionyl-l-carnitine</a> (<a href="http://www.wikidata.org/entity/Q5572581">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Gold_heptafluoride</td>
    <td>https://en.wikipedia.org/wiki/Gold_heptafluoride</td>
    <td><a href="https://scholia.toolforge.org/Q5578934">gold heptafluoride</a> (<a href="http://www.wikidata.org/entity/Q5578934">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Granatin_A</td>
    <td>https://en.wikipedia.org/wiki/Granatin_A</td>
    <td><a href="https://scholia.toolforge.org/Q5594157">Granatin A</a> (<a href="http://www.wikidata.org/entity/Q5594157">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Granatin_B</td>
    <td>https://en.wikipedia.org/wiki/Granatin_B</td>
    <td><a href="https://scholia.toolforge.org/Q5594160">Granatin B</a> (<a href="http://www.wikidata.org/entity/Q5594160">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Hydroxyethyl_methyl_cellulose</td>
    <td>https://en.wikipedia.org/wiki/Hydroxyethyl_methyl_cellulose</td>
    <td><a href="https://scholia.toolforge.org/Q5955578">Hydroxyethyl methyl cellulose</a> (<a href="http://www.wikidata.org/entity/Q5955578">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Scandium_dodecaboride</td>
    <td>https://en.wikipedia.org/wiki/Scandium_dodecaboride</td>
    <td><a href="https://scholia.toolforge.org/Q6129106">scandium dodecaboride</a> (<a href="http://www.wikidata.org/entity/Q6129106">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Magnesium_nickel_hydride</td>
    <td>https://en.wikipedia.org/wiki/Magnesium_nickel_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q6731397">Magnesium nickel hydride</a> (<a href="http://www.wikidata.org/entity/Q6731397">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Magnesium_polonide</td>
    <td>https://en.wikipedia.org/wiki/Magnesium_polonide</td>
    <td><a href="https://scholia.toolforge.org/Q6731402">magnesium polonide</a> (<a href="http://www.wikidata.org/entity/Q6731402">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Mutacin_1140</td>
    <td>https://en.wikipedia.org/wiki/Mutacin_1140</td>
    <td><a href="https://scholia.toolforge.org/Q6943638">mutacin 1140</a> (<a href="http://www.wikidata.org/entity/Q6943638">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/NBD-TMA</td>
    <td>https://en.wikipedia.org/wiki/NBD-TMA</td>
    <td><a href="https://scholia.toolforge.org/Q6952803">NBD-TMA</a> (<a href="http://www.wikidata.org/entity/Q6952803">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/NR58-3.14.3</td>
    <td>https://en.wikipedia.org/wiki/NR58-3.14.3</td>
    <td><a href="https://scholia.toolforge.org/Q6955100">NR58-3.14.3</a> (<a href="http://www.wikidata.org/entity/Q6955100">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Urodilatin</td>
    <td>https://en.wikipedia.org/wiki/Urodilatin</td>
    <td><a href="https://scholia.toolforge.org/Q6961789">Ularitide</a> (<a href="http://www.wikidata.org/entity/Q6961789">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nitrogen_pentafluoride</td>
    <td>https://en.wikipedia.org/wiki/Nitrogen_pentafluoride</td>
    <td><a href="https://scholia.toolforge.org/Q7041476">nitrogen pentafluoride</a> (<a href="http://www.wikidata.org/entity/Q7041476">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nitronium_perchlorate</td>
    <td>https://en.wikipedia.org/wiki/Nitronium_perchlorate</td>
    <td><a href="https://scholia.toolforge.org/Q7041493">nitronium perchlorate</a> (<a href="http://www.wikidata.org/entity/Q7041493">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Palladium_tetrafluoride</td>
    <td>https://en.wikipedia.org/wiki/Palladium_tetrafluoride</td>
    <td><a href="https://scholia.toolforge.org/Q7127719">palladium tetrafluoride</a> (<a href="http://www.wikidata.org/entity/Q7127719">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Pentaamine(dinitrogen)ruthenium(II)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Pentaamine(dinitrogen)ruthenium(II)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q7164918">pentaamine(dinitrogen)ruthenium(II) chloride</a> (<a href="http://www.wikidata.org/entity/Q7164918">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_dideuterium_phosphate</td>
    <td>https://en.wikipedia.org/wiki/Potassium_dideuterium_phosphate</td>
    <td><a href="https://scholia.toolforge.org/Q7234693">potassium dideuterium phosphate</a> (<a href="http://www.wikidata.org/entity/Q7234693">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_erythorbate</td>
    <td>https://en.wikipedia.org/wiki/Potassium_erythorbate</td>
    <td><a href="https://scholia.toolforge.org/Q7234694">potassium erythorbate</a> (<a href="http://www.wikidata.org/entity/Q7234694">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_dimanganate(III)</td>
    <td>https://en.wikipedia.org/wiki/Potassium_dimanganate(III)</td>
    <td><a href="https://scholia.toolforge.org/Q7234696">potassium dimanganate(III)</a> (<a href="http://www.wikidata.org/entity/Q7234696">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Psymberin</td>
    <td>https://en.wikipedia.org/wiki/Psymberin</td>
    <td><a href="https://scholia.toolforge.org/Q7256580">psymberin</a> (<a href="http://www.wikidata.org/entity/Q7256580">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zinc_pyrithione</td>
    <td>https://en.wikipedia.org/wiki/Zinc_pyrithione</td>
    <td><a href="https://scholia.toolforge.org/Q204602">pyrithione zinc</a> (<a href="http://www.wikidata.org/entity/Q204602">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Ruthenium_red</td>
    <td>https://en.wikipedia.org/wiki/Ruthenium_red</td>
    <td><a href="https://scholia.toolforge.org/Q424006">ruthenium red</a> (<a href="http://www.wikidata.org/entity/Q424006">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tantalum_hafnium_carbide</td>
    <td>https://en.wikipedia.org/wiki/Tantalum_hafnium_carbide</td>
    <td><a href="https://scholia.toolforge.org/Q424268">tantalum hafnium carbide</a> (<a href="http://www.wikidata.org/entity/Q424268">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Maitotoxin</td>
    <td>https://en.wikipedia.org/wiki/Maitotoxin</td>
    <td><a href="https://scholia.toolforge.org/Q425072">maitotoxin</a> (<a href="http://www.wikidata.org/entity/Q425072">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Rhenium_diboride</td>
    <td>https://en.wikipedia.org/wiki/Rhenium_diboride</td>
    <td><a href="https://scholia.toolforge.org/Q425164">rhenium diboride</a> (<a href="http://www.wikidata.org/entity/Q425164">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Brown_FK</td>
    <td>https://en.wikipedia.org/wiki/Brown_FK</td>
    <td><a href="https://scholia.toolforge.org/Q425437">brown FK</a> (<a href="http://www.wikidata.org/entity/Q425437">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tantalum_carbide</td>
    <td>https://en.wikipedia.org/wiki/Tantalum_carbide</td>
    <td><a href="https://scholia.toolforge.org/Q426498">tantalum carbide</a> (<a href="http://www.wikidata.org/entity/Q426498">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Americium(III)_bromide</td>
    <td>https://en.wikipedia.org/wiki/Americium(III)_bromide</td>
    <td><a href="https://scholia.toolforge.org/Q467634">americium(III) bromide</a> (<a href="http://www.wikidata.org/entity/Q467634">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Americium(III)_iodide</td>
    <td>https://en.wikipedia.org/wiki/Americium(III)_iodide</td>
    <td><a href="https://scholia.toolforge.org/Q467656">americium(III) iodide</a> (<a href="http://www.wikidata.org/entity/Q467656">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Dysprosium_titanate</td>
    <td>https://en.wikipedia.org/wiki/Dysprosium_titanate</td>
    <td><a href="https://scholia.toolforge.org/Q577230">dysprosium(III) titanate</a> (<a href="http://www.wikidata.org/entity/Q577230">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zirconium(III)_iodide</td>
    <td>https://en.wikipedia.org/wiki/Zirconium(III)_iodide</td>
    <td><a href="https://scholia.toolforge.org/Q205624">zirconium(III) iodide</a> (<a href="http://www.wikidata.org/entity/Q205624">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zirconium_tungstate</td>
    <td>https://en.wikipedia.org/wiki/Zirconium_tungstate</td>
    <td><a href="https://scholia.toolforge.org/Q205661">zirconium tungstate</a> (<a href="http://www.wikidata.org/entity/Q205661">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tungsten(III)_oxide</td>
    <td>https://en.wikipedia.org/wiki/Tungsten(III)_oxide</td>
    <td><a href="https://scholia.toolforge.org/Q379014">tungsten(III) oxide</a> (<a href="http://www.wikidata.org/entity/Q379014">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Triiron_dodecacarbonyl</td>
    <td>https://en.wikipedia.org/wiki/Triiron_dodecacarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q382703">triiron dodecacarbonyl</a> (<a href="http://www.wikidata.org/entity/Q382703">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Titanium_aluminide</td>
    <td>https://en.wikipedia.org/wiki/Titanium_aluminide</td>
    <td><a href="https://scholia.toolforge.org/Q408746">titanium aluminide</a> (<a href="http://www.wikidata.org/entity/Q408746">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nisin</td>
    <td>https://en.wikipedia.org/wiki/Nisin</td>
    <td><a href="https://scholia.toolforge.org/Q415798">nisin</a> (<a href="http://www.wikidata.org/entity/Q415798">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Collins_reagent</td>
    <td>https://en.wikipedia.org/wiki/Collins_reagent</td>
    <td><a href="https://scholia.toolforge.org/Q416217">Collins reagent</a> (<a href="http://www.wikidata.org/entity/Q416217">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cobalt_green</td>
    <td>https://en.wikipedia.org/wiki/Cobalt_green</td>
    <td><a href="https://scholia.toolforge.org/Q416459">cobalt green</a> (<a href="http://www.wikidata.org/entity/Q416459">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Silver_subfluoride</td>
    <td>https://en.wikipedia.org/wiki/Silver_subfluoride</td>
    <td><a href="https://scholia.toolforge.org/Q417478">silver subfluoride</a> (<a href="http://www.wikidata.org/entity/Q417478">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tetramethylammonium_pentafluoroxenate</td>
    <td>https://en.wikipedia.org/wiki/Tetramethylammonium_pentafluoroxenate</td>
    <td><a href="https://scholia.toolforge.org/Q511638">tetramethylammonium pentafluoroxenate</a> (<a href="http://www.wikidata.org/entity/Q511638">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Curdlan</td>
    <td>https://en.wikipedia.org/wiki/Curdlan</td>
    <td><a href="https://scholia.toolforge.org/Q616242">curdlan</a> (<a href="http://www.wikidata.org/entity/Q616242">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cobratoxin</td>
    <td>https://en.wikipedia.org/wiki/Cobratoxin</td>
    <td><a href="https://scholia.toolforge.org/Q661977">cobratoxin</a> (<a href="http://www.wikidata.org/entity/Q661977">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tin(IV)_fluoride</td>
    <td>https://en.wikipedia.org/wiki/Tin(IV)_fluoride</td>
    <td><a href="https://scholia.toolforge.org/Q204994">tin(IV) fluoride</a> (<a href="http://www.wikidata.org/entity/Q204994">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nitrostarch</td>
    <td>https://en.wikipedia.org/wiki/Nitrostarch</td>
    <td><a href="https://scholia.toolforge.org/Q774946">nitrostarch</a> (<a href="http://www.wikidata.org/entity/Q774946">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Boron_arsenide</td>
    <td>https://en.wikipedia.org/wiki/Boron_arsenide</td>
    <td><a href="https://scholia.toolforge.org/Q866825">boron arsenide</a> (<a href="http://www.wikidata.org/entity/Q866825">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithopone</td>
    <td>https://en.wikipedia.org/wiki/Lithopone</td>
    <td><a href="https://scholia.toolforge.org/Q899314">Lithopone</a> (<a href="http://www.wikidata.org/entity/Q899314">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Californium(III)_oxychloride</td>
    <td>https://en.wikipedia.org/wiki/Californium(III)_oxychloride</td>
    <td><a href="https://scholia.toolforge.org/Q904529">californium oxychloride</a> (<a href="http://www.wikidata.org/entity/Q904529">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Chrysolaminarin</td>
    <td>https://en.wikipedia.org/wiki/Chrysolaminarin</td>
    <td><a href="https://scholia.toolforge.org/Q906080">chrysolaminarin</a> (<a href="http://www.wikidata.org/entity/Q906080">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Copper(II)_acetylacetonate</td>
    <td>https://en.wikipedia.org/wiki/Copper(II)_acetylacetonate</td>
    <td><a href="https://scholia.toolforge.org/Q1792796">copper(II) acetylacetonate</a> (<a href="http://www.wikidata.org/entity/Q1792796">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Thallium_triiodide</td>
    <td>https://en.wikipedia.org/wiki/Thallium_triiodide</td>
    <td><a href="https://scholia.toolforge.org/Q2059737">thallium triiodide</a> (<a href="http://www.wikidata.org/entity/Q2059737">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Pectic_acid</td>
    <td>https://en.wikipedia.org/wiki/Pectic_acid</td>
    <td><a href="https://scholia.toolforge.org/Q2069698">pectic acid</a> (<a href="http://www.wikidata.org/entity/Q2069698">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Palladium_on_carbon</td>
    <td>https://en.wikipedia.org/wiki/Palladium_on_carbon</td>
    <td><a href="https://scholia.toolforge.org/Q2185009">palladium on carbon</a> (<a href="http://www.wikidata.org/entity/Q2185009">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/PEDOT-TMA</td>
    <td>https://en.wikipedia.org/wiki/PEDOT-TMA</td>
    <td><a href="https://scholia.toolforge.org/Q2219589">PEDOT-TMA</a> (<a href="http://www.wikidata.org/entity/Q2219589">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iron(III)_acetate</td>
    <td>https://en.wikipedia.org/wiki/Iron(III)_acetate</td>
    <td><a href="https://scholia.toolforge.org/Q2230936">basic iron(III) acetate</a> (<a href="http://www.wikidata.org/entity/Q2230936">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Carboxyhemoglobin</td>
    <td>https://en.wikipedia.org/wiki/Carboxyhemoglobin</td>
    <td><a href="https://scholia.toolforge.org/Q2259181">carboxyhemoglobin</a> (<a href="http://www.wikidata.org/entity/Q2259181">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_superoxide</td>
    <td>https://en.wikipedia.org/wiki/Lithium_superoxide</td>
    <td><a href="https://scholia.toolforge.org/Q2293867">lithium superoxide</a> (<a href="http://www.wikidata.org/entity/Q2293867">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Acetylated_distarch_adipate</td>
    <td>https://en.wikipedia.org/wiki/Acetylated_distarch_adipate</td>
    <td><a href="https://scholia.toolforge.org/Q2824457">acetylated distarch adipate</a> (<a href="http://www.wikidata.org/entity/Q2824457">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iridium_tetroxide</td>
    <td>https://en.wikipedia.org/wiki/Iridium_tetroxide</td>
    <td><a href="https://scholia.toolforge.org/Q2858011">iridium tetroxide</a> (<a href="http://www.wikidata.org/entity/Q2858011">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Protonated_hydrogen_cyanide</td>
    <td>https://en.wikipedia.org/wiki/Protonated_hydrogen_cyanide</td>
    <td><a href="https://scholia.toolforge.org/Q3008064">protonated hydrogen cyanide</a> (<a href="http://www.wikidata.org/entity/Q3008064">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Terbium_silicide</td>
    <td>https://en.wikipedia.org/wiki/Terbium_silicide</td>
    <td><a href="https://scholia.toolforge.org/Q3867223">terbium silicide</a> (<a href="http://www.wikidata.org/entity/Q3867223">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Quercitannic_acid</td>
    <td>https://en.wikipedia.org/wiki/Quercitannic_acid</td>
    <td><a href="https://scholia.toolforge.org/Q7271322">quercitannic acid</a> (<a href="http://www.wikidata.org/entity/Q7271322">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Trimethylenemethane</td>
    <td>https://en.wikipedia.org/wiki/Trimethylenemethane</td>
    <td><a href="https://scholia.toolforge.org/Q7842213">trimethylenemethane</a> (<a href="http://www.wikidata.org/entity/Q7842213">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Uranium(IV)_hydride</td>
    <td>https://en.wikipedia.org/wiki/Uranium(IV)_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q7899659">uranium(IV) hydride</a> (<a href="http://www.wikidata.org/entity/Q7899659">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Uranium_hexachloride</td>
    <td>https://en.wikipedia.org/wiki/Uranium_hexachloride</td>
    <td><a href="https://scholia.toolforge.org/Q7899678">uranium hexachloride</a> (<a href="http://www.wikidata.org/entity/Q7899678">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Uranium_hexoxide</td>
    <td>https://en.wikipedia.org/wiki/Uranium_hexoxide</td>
    <td><a href="https://scholia.toolforge.org/Q7899679">Uranium hexoxide</a> (<a href="http://www.wikidata.org/entity/Q7899679">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Uranium_monosulfide</td>
    <td>https://en.wikipedia.org/wiki/Uranium_monosulfide</td>
    <td><a href="https://scholia.toolforge.org/Q7899700">uranium monosulfide</a> (<a href="http://www.wikidata.org/entity/Q7899700">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Uranium_monophosphide</td>
    <td>https://en.wikipedia.org/wiki/Uranium_monophosphide</td>
    <td><a href="https://scholia.toolforge.org/Q7899701">uranium monophosphide</a> (<a href="http://www.wikidata.org/entity/Q7899701">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Uranium_pentachloride</td>
    <td>https://en.wikipedia.org/wiki/Uranium_pentachloride</td>
    <td><a href="https://scholia.toolforge.org/Q7899704">uranium pentachloride</a> (<a href="http://www.wikidata.org/entity/Q7899704">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Vanillotoxin</td>
    <td>https://en.wikipedia.org/wiki/Vanillotoxin</td>
    <td><a href="https://scholia.toolforge.org/Q7914938">Vanillotoxin</a> (<a href="http://www.wikidata.org/entity/Q7914938">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Welan_gum</td>
    <td>https://en.wikipedia.org/wiki/Welan_gum</td>
    <td><a href="https://scholia.toolforge.org/Q7980494">welan gum</a> (<a href="http://www.wikidata.org/entity/Q7980494">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zinc_L-aspartate</td>
    <td>https://en.wikipedia.org/wiki/Zinc_L-aspartate</td>
    <td><a href="https://scholia.toolforge.org/Q8072280">zinc L-aspartate</a> (<a href="http://www.wikidata.org/entity/Q8072280">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zinc_borate</td>
    <td>https://en.wikipedia.org/wiki/Zinc_borate</td>
    <td><a href="https://scholia.toolforge.org/Q8072284">zinc borate</a> (<a href="http://www.wikidata.org/entity/Q8072284">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zinc_chloride_hydroxide_monohydrate</td>
    <td>https://en.wikipedia.org/wiki/Zinc_chloride_hydroxide_monohydrate</td>
    <td><a href="https://scholia.toolforge.org/Q8072293">zinc chloride hydroxide monohydrate</a> (<a href="http://www.wikidata.org/entity/Q8072293">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Zirconium_propionate</td>
    <td>https://en.wikipedia.org/wiki/Zirconium_propionate</td>
    <td><a href="https://scholia.toolforge.org/Q8072754">Zirconium propanoate</a> (<a href="http://www.wikidata.org/entity/Q8072754">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_octachlorodirhenate</td>
    <td>https://en.wikipedia.org/wiki/Potassium_octachlorodirhenate</td>
    <td><a href="https://scholia.toolforge.org/Q10892265">potassium octachlorodirhenate</a> (<a href="http://www.wikidata.org/entity/Q10892265">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Carbon_hexoxide</td>
    <td>https://en.wikipedia.org/wiki/Carbon_hexoxide</td>
    <td><a href="https://scholia.toolforge.org/Q10893339">carbon hexoxide</a> (<a href="http://www.wikidata.org/entity/Q10893339">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Protactinium(IV)_bromide</td>
    <td>https://en.wikipedia.org/wiki/Protactinium(IV)_bromide</td>
    <td><a href="https://scholia.toolforge.org/Q10925175">protactinium(IV) bromide</a> (<a href="http://www.wikidata.org/entity/Q10925175">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_ferrooxalate</td>
    <td>https://en.wikipedia.org/wiki/Potassium_ferrooxalate</td>
    <td><a href="https://scholia.toolforge.org/Q12438852">potassium ferrooxalate</a> (<a href="http://www.wikidata.org/entity/Q12438852">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_polonide</td>
    <td>https://en.wikipedia.org/wiki/Potassium_polonide</td>
    <td><a href="https://scholia.toolforge.org/Q13518697">potassium polonide</a> (<a href="http://www.wikidata.org/entity/Q13518697">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_chlorochromate</td>
    <td>https://en.wikipedia.org/wiki/Potassium_chlorochromate</td>
    <td><a href="https://scholia.toolforge.org/Q13582207">potassium chlorochromate</a> (<a href="http://www.wikidata.org/entity/Q13582207">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Copper_indium_gallium_selenide</td>
    <td>https://en.wikipedia.org/wiki/Copper_indium_gallium_selenide</td>
    <td><a href="https://scholia.toolforge.org/Q15023366">Copper indium gallium selenide</a> (<a href="http://www.wikidata.org/entity/Q15023366">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iron_tetraboride</td>
    <td>https://en.wikipedia.org/wiki/Iron_tetraboride</td>
    <td><a href="https://scholia.toolforge.org/Q15229397">iron tetraboride</a> (<a href="http://www.wikidata.org/entity/Q15229397">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cornusiin_E</td>
    <td>https://en.wikipedia.org/wiki/Cornusiin_E</td>
    <td><a href="https://scholia.toolforge.org/Q15410921">Cornusiin E</a> (<a href="http://www.wikidata.org/entity/Q15410921">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Epimerox</td>
    <td>https://en.wikipedia.org/wiki/Epimerox</td>
    <td><a href="https://scholia.toolforge.org/Q15410944">Epimerox</a> (<a href="http://www.wikidata.org/entity/Q15410944">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Gadolinium_acetylacetonate</td>
    <td>https://en.wikipedia.org/wiki/Gadolinium_acetylacetonate</td>
    <td><a href="https://scholia.toolforge.org/Q15410965">gadolinium acetylacetonate</a> (<a href="http://www.wikidata.org/entity/Q15410965">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Protactinium(V)_bromide</td>
    <td>https://en.wikipedia.org/wiki/Protactinium(V)_bromide</td>
    <td><a href="https://scholia.toolforge.org/Q17325761">protactinium(V) bromide</a> (<a href="http://www.wikidata.org/entity/Q17325761">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Protactinium(V)_iodide</td>
    <td>https://en.wikipedia.org/wiki/Protactinium(V)_iodide</td>
    <td><a href="https://scholia.toolforge.org/Q17325762">protactinium(V) iodide</a> (<a href="http://www.wikidata.org/entity/Q17325762">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_tetrahydridogallate</td>
    <td>https://en.wikipedia.org/wiki/Lithium_tetrahydridogallate</td>
    <td><a href="https://scholia.toolforge.org/Q17361161">lithium tetrahydridogallate</a> (<a href="http://www.wikidata.org/entity/Q17361161">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cerium(III)_methanesulfonate</td>
    <td>https://en.wikipedia.org/wiki/Cerium(III)_methanesulfonate</td>
    <td><a href="https://scholia.toolforge.org/Q18205916">cerium(III) methanesulfonate</a> (<a href="http://www.wikidata.org/entity/Q18205916">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Copper_peroxide</td>
    <td>https://en.wikipedia.org/wiki/Copper_peroxide</td>
    <td><a href="https://scholia.toolforge.org/Q18211793">copper peroxide</a> (<a href="http://www.wikidata.org/entity/Q18211793">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Erbium(III)_nitrate</td>
    <td>https://en.wikipedia.org/wiki/Erbium(III)_nitrate</td>
    <td><a href="https://scholia.toolforge.org/Q18213085">erbium(III) nitrate</a> (<a href="http://www.wikidata.org/entity/Q18213085">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Thulium(III)_nitrate</td>
    <td>https://en.wikipedia.org/wiki/Thulium(III)_nitrate</td>
    <td><a href="https://scholia.toolforge.org/Q18213089">thulium(III) nitrate</a> (<a href="http://www.wikidata.org/entity/Q18213089">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cyphostemmin_B</td>
    <td>https://en.wikipedia.org/wiki/Cyphostemmin_B</td>
    <td><a href="https://scholia.toolforge.org/Q18349723">cyphostemmin B</a> (<a href="http://www.wikidata.org/entity/Q18349723">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Shvo_catalyst</td>
    <td>https://en.wikipedia.org/wiki/Shvo_catalyst</td>
    <td><a href="https://scholia.toolforge.org/Q4788036">Shvo catalyst</a> (<a href="http://www.wikidata.org/entity/Q4788036">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Scandium_monosulfide</td>
    <td>https://en.wikipedia.org/wiki/Scandium_monosulfide</td>
    <td><a href="https://scholia.toolforge.org/Q7429991">scandium monosulfide</a> (<a href="http://www.wikidata.org/entity/Q7429991">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Stenophyllanin_A</td>
    <td>https://en.wikipedia.org/wiki/Stenophyllanin_A</td>
    <td><a href="https://scholia.toolforge.org/Q7607715">Stenophyllanin A</a> (<a href="http://www.wikidata.org/entity/Q7607715">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tellurium_monoiodide</td>
    <td>https://en.wikipedia.org/wiki/Tellurium_monoiodide</td>
    <td><a href="https://scholia.toolforge.org/Q7697690">tellurium(I) iodide</a> (<a href="http://www.wikidata.org/entity/Q7697690">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_polonide</td>
    <td>https://en.wikipedia.org/wiki/Lithium_polonide</td>
    <td><a href="https://scholia.toolforge.org/Q7789180">lithium polonide</a> (<a href="http://www.wikidata.org/entity/Q7789180">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/ADDA_(amino_acid)</td>
    <td>https://en.wikipedia.org/wiki/ADDA_(amino_acid)</td>
    <td><a href="https://scholia.toolforge.org/Q9137074">ADDA</a> (<a href="http://www.wikidata.org/entity/Q9137074">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_dithioferrate</td>
    <td>https://en.wikipedia.org/wiki/Potassium_dithioferrate</td>
    <td><a href="https://scholia.toolforge.org/Q15628174">potassium dithioferrate</a> (<a href="http://www.wikidata.org/entity/Q15628174">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Hexaborane(12)</td>
    <td>https://en.wikipedia.org/wiki/Hexaborane(12)</td>
    <td><a href="https://scholia.toolforge.org/Q15628412">hexaborane(12)</a> (<a href="http://www.wikidata.org/entity/Q15628412">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Osmium_pentafluoride</td>
    <td>https://en.wikipedia.org/wiki/Osmium_pentafluoride</td>
    <td><a href="https://scholia.toolforge.org/Q15632747">osmium(V) fluoride</a> (<a href="http://www.wikidata.org/entity/Q15632747">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Samarium(II)_fluoride</td>
    <td>https://en.wikipedia.org/wiki/Samarium(II)_fluoride</td>
    <td><a href="https://scholia.toolforge.org/Q15632780">samarium(II) fluoride</a> (<a href="http://www.wikidata.org/entity/Q15632780">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Agatolimod</td>
    <td>https://en.wikipedia.org/wiki/Agatolimod</td>
    <td><a href="https://scholia.toolforge.org/Q15633941">agatolimod</a> (<a href="http://www.wikidata.org/entity/Q15633941">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Aganirsen</td>
    <td>https://en.wikipedia.org/wiki/Aganirsen</td>
    <td><a href="https://scholia.toolforge.org/Q15633943">aganirsen</a> (<a href="http://www.wikidata.org/entity/Q15633943">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Trimethylsilyl_cyclopentadiene</td>
    <td>https://en.wikipedia.org/wiki/Trimethylsilyl_cyclopentadiene</td>
    <td><a href="https://scholia.toolforge.org/Q15634158">Trimethylsilyl cyclopentadiene</a> (<a href="http://www.wikidata.org/entity/Q15634158">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bis(dinitrogen)bis(1,2-bis(diphenylphosphino)ethane)molybdenum(0)</td>
    <td>https://en.wikipedia.org/wiki/Bis(dinitrogen)bis(1,2-bis(diphenylphosphino)ethane)molybdenum(0)</td>
    <td><a href="https://scholia.toolforge.org/Q15634210">Bis(dinitrogen)bis(1,2-bis(diphenylphosphino)ethane)molybdenum(0)</a> (<a href="http://www.wikidata.org/entity/Q15634210">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/3,5-Dimethylpiperidine</td>
    <td>https://en.wikipedia.org/wiki/3,5-Dimethylpiperidine</td>
    <td><a href="https://scholia.toolforge.org/Q15634223">3,5-dimethylpiperidine</a> (<a href="http://www.wikidata.org/entity/Q15634223">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Pseudopterosin_E</td>
    <td>https://en.wikipedia.org/wiki/Pseudopterosin_E</td>
    <td><a href="https://scholia.toolforge.org/Q15634229">Pseudopterosin E</a> (<a href="http://www.wikidata.org/entity/Q15634229">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Magnesium_iron_hexahydride</td>
    <td>https://en.wikipedia.org/wiki/Magnesium_iron_hexahydride</td>
    <td><a href="https://scholia.toolforge.org/Q15634287">magnesium iron hexahydride</a> (<a href="http://www.wikidata.org/entity/Q15634287">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Prodelphinidin_C2</td>
    <td>https://en.wikipedia.org/wiki/Prodelphinidin_C2</td>
    <td><a href="https://scholia.toolforge.org/Q15634380">Prodelphinidin C2</a> (<a href="http://www.wikidata.org/entity/Q15634380">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Prodelphinidin_B9</td>
    <td>https://en.wikipedia.org/wiki/Prodelphinidin_B9</td>
    <td><a href="https://scholia.toolforge.org/Q15634381">Prodelphinidin B9</a> (<a href="http://www.wikidata.org/entity/Q15634381">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cerium_diiodide</td>
    <td>https://en.wikipedia.org/wiki/Cerium_diiodide</td>
    <td><a href="https://scholia.toolforge.org/Q16830827">cerium diiodide</a> (<a href="http://www.wikidata.org/entity/Q16830827">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Gadolinium_diiodide</td>
    <td>https://en.wikipedia.org/wiki/Gadolinium_diiodide</td>
    <td><a href="https://scholia.toolforge.org/Q16831506">gadolinium diiodide</a> (<a href="http://www.wikidata.org/entity/Q16831506">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Praseodymium_diiodide</td>
    <td>https://en.wikipedia.org/wiki/Praseodymium_diiodide</td>
    <td><a href="https://scholia.toolforge.org/Q16855776">praseodymium diiodide</a> (<a href="http://www.wikidata.org/entity/Q16855776">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Galtamycin_B</td>
    <td>https://en.wikipedia.org/wiki/Galtamycin_B</td>
    <td><a href="https://scholia.toolforge.org/Q16897069">galtamycin B</a> (<a href="http://www.wikidata.org/entity/Q16897069">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/JV-1-36</td>
    <td>https://en.wikipedia.org/wiki/JV-1-36</td>
    <td><a href="https://scholia.toolforge.org/Q16920100">JV-1-36</a> (<a href="http://www.wikidata.org/entity/Q16920100">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bis(triphenylphosphine)platinum_chloride</td>
    <td>https://en.wikipedia.org/wiki/Bis(triphenylphosphine)platinum_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q17005128">bis(triphenylphosphine)platinum chloride</a> (<a href="http://www.wikidata.org/entity/Q17005128">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lutetium_phosphide</td>
    <td>https://en.wikipedia.org/wiki/Lutetium_phosphide</td>
    <td><a href="https://scholia.toolforge.org/Q17057347">lutetium phosphide</a> (<a href="http://www.wikidata.org/entity/Q17057347">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tetramesityldiiron</td>
    <td>https://en.wikipedia.org/wiki/Tetramesityldiiron</td>
    <td><a href="https://scholia.toolforge.org/Q17121628">Tetramesityldiiron</a> (<a href="http://www.wikidata.org/entity/Q17121628">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Curium(III)_fluoride</td>
    <td>https://en.wikipedia.org/wiki/Curium(III)_fluoride</td>
    <td><a href="https://scholia.toolforge.org/Q1144604">curium(III) fluoride</a> (<a href="http://www.wikidata.org/entity/Q1144604">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Beryllium_azide</td>
    <td>https://en.wikipedia.org/wiki/Beryllium_azide</td>
    <td><a href="https://scholia.toolforge.org/Q4896099">beryllium azide</a> (<a href="http://www.wikidata.org/entity/Q4896099">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bismuth_silicon_oxide</td>
    <td>https://en.wikipedia.org/wiki/Bismuth_silicon_oxide</td>
    <td><a href="https://scholia.toolforge.org/Q4918352">bismuth silicon oxide</a> (<a href="http://www.wikidata.org/entity/Q4918352">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cadmium(I)_tetrachloroaluminate</td>
    <td>https://en.wikipedia.org/wiki/Cadmium(I)_tetrachloroaluminate</td>
    <td><a href="https://scholia.toolforge.org/Q5016546">cadmium(I) tetrachloroaluminate</a> (<a href="http://www.wikidata.org/entity/Q5016546">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_cadmium_bromide</td>
    <td>https://en.wikipedia.org/wiki/Caesium_cadmium_bromide</td>
    <td><a href="https://scholia.toolforge.org/Q5017045">caesium cadmium bromide</a> (<a href="http://www.wikidata.org/entity/Q5017045">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_cadmium_chloride</td>
    <td>https://en.wikipedia.org/wiki/Caesium_cadmium_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q5017047">caesium cadmium chloride</a> (<a href="http://www.wikidata.org/entity/Q5017047">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_dodecaborate</td>
    <td>https://en.wikipedia.org/wiki/Caesium_dodecaborate</td>
    <td><a href="https://scholia.toolforge.org/Q5017048">caesium dodecaborate</a> (<a href="http://www.wikidata.org/entity/Q5017048">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_hexafluorocobaltate(IV)</td>
    <td>https://en.wikipedia.org/wiki/Caesium_hexafluorocobaltate(IV)</td>
    <td><a href="https://scholia.toolforge.org/Q5017049">caesium hexafluorocobaltate(IV)</a> (<a href="http://www.wikidata.org/entity/Q5017049">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_lithium_borate</td>
    <td>https://en.wikipedia.org/wiki/Caesium_lithium_borate</td>
    <td><a href="https://scholia.toolforge.org/Q5017050">caesium lithium borate</a> (<a href="http://www.wikidata.org/entity/Q5017050">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_hexafluorocuprate(IV)</td>
    <td>https://en.wikipedia.org/wiki/Caesium_hexafluorocuprate(IV)</td>
    <td><a href="https://scholia.toolforge.org/Q5017051">caesium hexafluorocuprate(IV)</a> (<a href="http://www.wikidata.org/entity/Q5017051">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Calcium_copper_titanate</td>
    <td>https://en.wikipedia.org/wiki/Calcium_copper_titanate</td>
    <td><a href="https://scholia.toolforge.org/Q5018824">Calcium copper titanate</a> (<a href="http://www.wikidata.org/entity/Q5018824">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Chromium(I)_hydride</td>
    <td>https://en.wikipedia.org/wiki/Chromium(I)_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q5113812">Chromium(I) hydride</a> (<a href="http://www.wikidata.org/entity/Q5113812">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Chromium(II)_hydride</td>
    <td>https://en.wikipedia.org/wiki/Chromium(II)_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q5113814">chromium(II) hydride</a> (<a href="http://www.wikidata.org/entity/Q5113814">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Chromium_acetate_hydroxide</td>
    <td>https://en.wikipedia.org/wiki/Chromium_acetate_hydroxide</td>
    <td><a href="https://scholia.toolforge.org/Q5113827">chromium acetate hydroxide</a> (<a href="http://www.wikidata.org/entity/Q5113827">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cinchotannic_acid</td>
    <td>https://en.wikipedia.org/wiki/Cinchotannic_acid</td>
    <td><a href="https://scholia.toolforge.org/Q5120194">Cinchotannic acid</a> (<a href="http://www.wikidata.org/entity/Q5120194">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cobatoxin</td>
    <td>https://en.wikipedia.org/wiki/Cobatoxin</td>
    <td><a href="https://scholia.toolforge.org/Q5138732">Cobatoxin</a> (<a href="http://www.wikidata.org/entity/Q5138732">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Convallarin</td>
    <td>https://en.wikipedia.org/wiki/Convallarin</td>
    <td><a href="https://scholia.toolforge.org/Q5166116">convallarin</a> (<a href="http://www.wikidata.org/entity/Q5166116">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Copper_ibuprofenate</td>
    <td>https://en.wikipedia.org/wiki/Copper_ibuprofenate</td>
    <td><a href="https://scholia.toolforge.org/Q5168779">Copper ibuprofenate</a> (<a href="http://www.wikidata.org/entity/Q5168779">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cyclobutadieneiron_tricarbonyl</td>
    <td>https://en.wikipedia.org/wiki/Cyclobutadieneiron_tricarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q5198676">Cyclobutadieneiron tricarbonyl</a> (<a href="http://www.wikidata.org/entity/Q5198676">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cyclooctatetraenide_anion</td>
    <td>https://en.wikipedia.org/wiki/Cyclooctatetraenide_anion</td>
    <td><a href="https://scholia.toolforge.org/Q5198907">cyclooctatetraenide anion</a> (<a href="http://www.wikidata.org/entity/Q5198907">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cyclopentadienylcobalt_dicarbonyl</td>
    <td>https://en.wikipedia.org/wiki/Cyclopentadienylcobalt_dicarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q5198926">cyclopentadienylcobalt dicarbonyl</a> (<a href="http://www.wikidata.org/entity/Q5198926">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cyclopentadienyl_allyl_palladium</td>
    <td>https://en.wikipedia.org/wiki/Cyclopentadienyl_allyl_palladium</td>
    <td><a href="https://scholia.toolforge.org/Q5198927">cyclopentadienyl allyl palladium</a> (<a href="http://www.wikidata.org/entity/Q5198927">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cyclopentadienyliron_dicarbonyl_iodide</td>
    <td>https://en.wikipedia.org/wiki/Cyclopentadienyliron_dicarbonyl_iodide</td>
    <td><a href="https://scholia.toolforge.org/Q5198928">Cyclopentadienyliron dicarbonyl iodide</a> (<a href="http://www.wikidata.org/entity/Q5198928">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/DEAE-Sepharose</td>
    <td>https://en.wikipedia.org/wiki/DEAE-Sepharose</td>
    <td><a href="https://scholia.toolforge.org/Q5204759">DEAE-Sepharose</a> (<a href="http://www.wikidata.org/entity/Q5204759">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Decamethyldizincocene</td>
    <td>https://en.wikipedia.org/wiki/Decamethyldizincocene</td>
    <td><a href="https://scholia.toolforge.org/Q5248734">Decamethyldizincocene</a> (<a href="http://www.wikidata.org/entity/Q5248734">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Epicutissimin_A</td>
    <td>https://en.wikipedia.org/wiki/Epicutissimin_A</td>
    <td><a href="https://scholia.toolforge.org/Q5382668">Epicutissimin A</a> (<a href="http://www.wikidata.org/entity/Q5382668">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Gallium_maltolate</td>
    <td>https://en.wikipedia.org/wiki/Gallium_maltolate</td>
    <td><a href="https://scholia.toolforge.org/Q5519111">Gallium maltolate</a> (<a href="http://www.wikidata.org/entity/Q5519111">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Leumorphin</td>
    <td>https://en.wikipedia.org/wiki/Leumorphin</td>
    <td><a href="https://scholia.toolforge.org/Q6534550">Leumorphin</a> (<a href="http://www.wikidata.org/entity/Q6534550">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Punicacortein_D</td>
    <td>https://en.wikipedia.org/wiki/Punicacortein_D</td>
    <td><a href="https://scholia.toolforge.org/Q7260200">punicacortein D</a> (<a href="http://www.wikidata.org/entity/Q7260200">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Berkelium(III)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Berkelium(III)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q820865">berkelium(III) chloride</a> (<a href="http://www.wikidata.org/entity/Q820865">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Berkelium(IV)_oxide</td>
    <td>https://en.wikipedia.org/wiki/Berkelium(IV)_oxide</td>
    <td><a href="https://scholia.toolforge.org/Q820876">berkelium(IV) oxide</a> (<a href="http://www.wikidata.org/entity/Q820876">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_superoxide</td>
    <td>https://en.wikipedia.org/wiki/Caesium_superoxide</td>
    <td><a href="https://scholia.toolforge.org/Q1025477">caesium superoxide</a> (<a href="http://www.wikidata.org/entity/Q1025477">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Caesium_ozonide</td>
    <td>https://en.wikipedia.org/wiki/Caesium_ozonide</td>
    <td><a href="https://scholia.toolforge.org/Q1025482">cesium ozonide</a> (<a href="http://www.wikidata.org/entity/Q1025482">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Californium(III)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Californium(III)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q1026968">californium(III) chloride</a> (<a href="http://www.wikidata.org/entity/Q1026968">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Californium(III)_oxyfluoride</td>
    <td>https://en.wikipedia.org/wiki/Californium(III)_oxyfluoride</td>
    <td><a href="https://scholia.toolforge.org/Q1026977">californium(III) oxyfluoride</a> (<a href="http://www.wikidata.org/entity/Q1026977">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Potassium_nonahydridorhenate</td>
    <td>https://en.wikipedia.org/wiki/Potassium_nonahydridorhenate</td>
    <td><a href="https://scholia.toolforge.org/Q1089194">potassium nonahydridorhenate</a> (<a href="http://www.wikidata.org/entity/Q1089194">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Lithium_imide</td>
    <td>https://en.wikipedia.org/wiki/Lithium_imide</td>
    <td><a href="https://scholia.toolforge.org/Q1090011">lithium imide</a> (<a href="http://www.wikidata.org/entity/Q1090011">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Strontium_nitride</td>
    <td>https://en.wikipedia.org/wiki/Strontium_nitride</td>
    <td><a href="https://scholia.toolforge.org/Q1091256">strontium nitride</a> (<a href="http://www.wikidata.org/entity/Q1091256">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Calcium(I)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Calcium(I)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q1096750">calcium(I) chloride</a> (<a href="http://www.wikidata.org/entity/Q1096750">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Curium(III)_chloride</td>
    <td>https://en.wikipedia.org/wiki/Curium(III)_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q1144605">curium(III) chloride</a> (<a href="http://www.wikidata.org/entity/Q1144605">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Promethium(III)_iodide</td>
    <td>https://en.wikipedia.org/wiki/Promethium(III)_iodide</td>
    <td><a href="https://scholia.toolforge.org/Q1473876">promethium(III) iodide</a> (<a href="http://www.wikidata.org/entity/Q1473876">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Promethium(III)_bromide</td>
    <td>https://en.wikipedia.org/wiki/Promethium(III)_bromide</td>
    <td><a href="https://scholia.toolforge.org/Q1547180">promethium(III) bromide</a> (<a href="http://www.wikidata.org/entity/Q1547180">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Promethium(III)_fluoride</td>
    <td>https://en.wikipedia.org/wiki/Promethium(III)_fluoride</td>
    <td><a href="https://scholia.toolforge.org/Q1796798">promethium(III) fluoride</a> (<a href="http://www.wikidata.org/entity/Q1796798">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Nickel_hydrazine_nitrate</td>
    <td>https://en.wikipedia.org/wiki/Nickel_hydrazine_nitrate</td>
    <td><a href="https://scholia.toolforge.org/Q1985626">nickel hydrazine nitrate</a> (<a href="http://www.wikidata.org/entity/Q1985626">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Niobium_carbide</td>
    <td>https://en.wikipedia.org/wiki/Niobium_carbide</td>
    <td><a href="https://scholia.toolforge.org/Q2348776">niobium carbide</a> (<a href="http://www.wikidata.org/entity/Q2348776">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Iridium_tetrafluoride</td>
    <td>https://en.wikipedia.org/wiki/Iridium_tetrafluoride</td>
    <td><a href="https://scholia.toolforge.org/Q2356808">iridium tetrafluoride</a> (<a href="http://www.wikidata.org/entity/Q2356808">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Tetrakis(1-norbornyl)cobalt(IV)</td>
    <td>https://en.wikipedia.org/wiki/Tetrakis(1-norbornyl)cobalt(IV)</td>
    <td><a href="https://scholia.toolforge.org/Q2406745">tetrakis(1-norbornyl)cobalt(IV)</a> (<a href="http://www.wikidata.org/entity/Q2406745">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Singlet_oxygen</td>
    <td>https://en.wikipedia.org/wiki/Singlet_oxygen</td>
    <td><a href="https://scholia.toolforge.org/Q2413613">singlet oxygen</a> (<a href="http://www.wikidata.org/entity/Q2413613">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Calcium_monophosphide</td>
    <td>https://en.wikipedia.org/wiki/Calcium_monophosphide</td>
    <td><a href="https://scholia.toolforge.org/Q2452235">calcium monophosphide</a> (<a href="http://www.wikidata.org/entity/Q2452235">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Hexol</td>
    <td>https://en.wikipedia.org/wiki/Hexol</td>
    <td><a href="https://scholia.toolforge.org/Q2462786">hexol</a> (<a href="http://www.wikidata.org/entity/Q2462786">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Propylene_glycol_alginate</td>
    <td>https://en.wikipedia.org/wiki/Propylene_glycol_alginate</td>
    <td><a href="https://scholia.toolforge.org/Q2474785">propylene glycol alginate</a> (<a href="http://www.wikidata.org/entity/Q2474785">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/(Benzylideneacetone)iron_tricarbonyl</td>
    <td>https://en.wikipedia.org/wiki/(Benzylideneacetone)iron_tricarbonyl</td>
    <td><a href="https://scholia.toolforge.org/Q2613093">(benzylideneacetone)iron tricarbonyl</a> (<a href="http://www.wikidata.org/entity/Q2613093">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Graphane</td>
    <td>https://en.wikipedia.org/wiki/Graphane</td>
    <td><a href="https://scholia.toolforge.org/Q2660535">graphane</a> (<a href="http://www.wikidata.org/entity/Q2660535">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cellulose_diacetate</td>
    <td>https://en.wikipedia.org/wiki/Cellulose_diacetate</td>
    <td><a href="https://scholia.toolforge.org/Q3025842">cellulose diacetate</a> (<a href="http://www.wikidata.org/entity/Q3025842">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Gallocatechol</td>
    <td>https://en.wikipedia.org/wiki/Gallocatechol</td>
    <td><a href="https://scholia.toolforge.org/Q3044728">gallocatechol</a> (<a href="http://www.wikidata.org/entity/Q3044728">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Bismuth_ferrite</td>
    <td>https://en.wikipedia.org/wiki/Bismuth_ferrite</td>
    <td><a href="https://scholia.toolforge.org/Q3069714">bismuth ferrite</a> (<a href="http://www.wikidata.org/entity/Q3069714">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Actinium(III)_fluoride</td>
    <td>https://en.wikipedia.org/wiki/Actinium(III)_fluoride</td>
    <td><a href="https://scholia.toolforge.org/Q3074510">actinium fluoride</a> (<a href="http://www.wikidata.org/entity/Q3074510">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Actinium(III)_iodide</td>
    <td>https://en.wikipedia.org/wiki/Actinium(III)_iodide</td>
    <td><a href="https://scholia.toolforge.org/Q3154067">actinium triiodide</a> (<a href="http://www.wikidata.org/entity/Q3154067">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Uranium_nitrides</td>
    <td>https://en.wikipedia.org/wiki/Uranium_nitrides</td>
    <td><a href="https://scholia.toolforge.org/Q3181207">diuranium trinitride</a> (<a href="http://www.wikidata.org/entity/Q3181207">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Chlorinated_polyvinyl_chloride</td>
    <td>https://en.wikipedia.org/wiki/Chlorinated_polyvinyl_chloride</td>
    <td><a href="https://scholia.toolforge.org/Q3395510">chlorinated polyvinyl chloride</a> (<a href="http://www.wikidata.org/entity/Q3395510">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cadmium_hydride</td>
    <td>https://en.wikipedia.org/wiki/Cadmium_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q3462573">cadmium hydride</a> (<a href="http://www.wikidata.org/entity/Q3462573">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Triplet_oxygen</td>
    <td>https://en.wikipedia.org/wiki/Triplet_oxygen</td>
    <td><a href="https://scholia.toolforge.org/Q3497595">triplet oxygen</a> (<a href="http://www.wikidata.org/entity/Q3497595">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Actinium(III)_sulfide</td>
    <td>https://en.wikipedia.org/wiki/Actinium(III)_sulfide</td>
    <td><a href="https://scholia.toolforge.org/Q3539686">actinium(III) sulfide</a> (<a href="http://www.wikidata.org/entity/Q3539686">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Boron_suboxide</td>
    <td>https://en.wikipedia.org/wiki/Boron_suboxide</td>
    <td><a href="https://scholia.toolforge.org/Q4120057">Boron suboxide</a> (<a href="http://www.wikidata.org/entity/Q4120057">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Strontium_hydride</td>
    <td>https://en.wikipedia.org/wiki/Strontium_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q4138050">strontium hydride</a> (<a href="http://www.wikidata.org/entity/Q4138050">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Cobalt(II)_hydride</td>
    <td>https://en.wikipedia.org/wiki/Cobalt(II)_hydride</td>
    <td><a href="https://scholia.toolforge.org/Q4161299">cobalt(II) hydride</a> (<a href="http://www.wikidata.org/entity/Q4161299">edit</a>)</td>
  </tr>
  <tr>
    <td>http://dbpedia.org/resource/Molybdenum_dichloride_dioxide</td>
    <td>https://en.wikipedia.org/wiki/Molybdenum_dichloride_dioxide</td>
    <td><a href="https://scholia.toolforge.org/Q4161974">molybdenum dichloride dioxide</a> (<a href="http://www.wikidata.org/entity/Q4161974">edit</a>)</td>
  </tr>
</table>
## Code examples
### curl
```shell
curl -o missingSMILES.rq https://raw.githubusercontent.com/egonw/SARS-CoV-2-Queries/master/sparql/missingSMILES.rq
curl -H "Accept: text/tab-separated-values" -G https://query.wikidata.org/bigdata/namespace/wdq/sparql --data-urlencode query@missingSMILES.rq
```
This SPARQL query is available under CCZero.
