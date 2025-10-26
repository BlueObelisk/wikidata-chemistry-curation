# polymersWithoutCXSMILES.rq
**Code examples:** [curl](#curl)
### SPARQL
```sparql
SELECT ?cmp ?cmpLabel WHERE {
  ?cmp wdt:P31 wd:Q81163 .
  MINUS { ?cmp wdt:P10718 [] }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```
[Execute](https://query.wikidata.org/embed.html#SELECT%20%3Fcmp%20%3FcmpLabel%20WHERE%20%7B%0A%20%20%3Fcmp%20wdt%3AP31%20wd%3AQ81163%20.%0A%20%20MINUS%20%7B%20%3Fcmp%20wdt%3AP10718%20%5B%5D%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A) or [Edit](https://query.wikidata.org/#SELECT%20%3Fcmp%20%3FcmpLabel%20WHERE%20%7B%0A%20%20%3Fcmp%20wdt%3AP31%20wd%3AQ81163%20.%0A%20%20MINUS%20%7B%20%3Fcmp%20wdt%3AP10718%20%5B%5D%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A)


### Output
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
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q410200">ficoll</a> (<a href="http://www.wikidata.org/entity/Q410200">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q411341">diethylaminoethyl cellulose</a> (<a href="http://www.wikidata.org/entity/Q411341">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q420113">ethyl cellulose</a> (<a href="http://www.wikidata.org/entity/Q420113">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q421690">PEDOT:PSS</a> (<a href="http://www.wikidata.org/entity/Q421690">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q424668">heparan sulfate</a> (<a href="http://www.wikidata.org/entity/Q424668">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q637756">Synthetic ice</a> (<a href="http://www.wikidata.org/entity/Q637756">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q781350">lipoteichoic acid</a> (<a href="http://www.wikidata.org/entity/Q781350">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q900292">Hypalon</a> (<a href="http://www.wikidata.org/entity/Q900292">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q1035763">Cardo polymer</a> (<a href="http://www.wikidata.org/entity/Q1035763">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q2102931">polymeric diphenylmethane diisocyanate</a> (<a href="http://www.wikidata.org/entity/Q2102931">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q2504005">polyoctenamer</a> (<a href="http://www.wikidata.org/entity/Q2504005">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q2666962">cross-linked polyethylene</a> (<a href="http://www.wikidata.org/entity/Q2666962">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q3588152">cold enamel</a> (<a href="http://www.wikidata.org/entity/Q3588152">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q3748146">formazine</a> (<a href="http://www.wikidata.org/entity/Q3748146">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q3888260">Q3888260</a> (<a href="http://www.wikidata.org/entity/Q3888260">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q4369965">poly-cotton</a> (<a href="http://www.wikidata.org/entity/Q4369965">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q4383827">Pural</a> (<a href="http://www.wikidata.org/entity/Q4383827">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q4493247">fluoroelastomer</a> (<a href="http://www.wikidata.org/entity/Q4493247">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q5353579">elastolefin</a> (<a href="http://www.wikidata.org/entity/Q5353579">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q5462608">Flubber</a> (<a href="http://www.wikidata.org/entity/Q5462608">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q5597232">graphitic carbon nitride</a> (<a href="http://www.wikidata.org/entity/Q5597232">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q7205569">Pluronic P-123</a> (<a href="http://www.wikidata.org/entity/Q7205569">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q7226092">Poly(hydridocarbyne)</a> (<a href="http://www.wikidata.org/entity/Q7226092">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q7226142">polyaniline nanofibers</a> (<a href="http://www.wikidata.org/entity/Q7226142">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q7226747">Polyphenyl ether</a> (<a href="http://www.wikidata.org/entity/Q7226747">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q7695787">Telechelic polymer</a> (<a href="http://www.wikidata.org/entity/Q7695787">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q12378730">vinyl mix for stamping records</a> (<a href="http://www.wikidata.org/entity/Q12378730">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q16681178">Tritan</a> (<a href="http://www.wikidata.org/entity/Q16681178">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q16929866">Thiokol</a> (<a href="http://www.wikidata.org/entity/Q16929866">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q16944492">Nylon 4</a> (<a href="http://www.wikidata.org/entity/Q16944492">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q17145661">IPK acrylic-polyvinyl chloride</a> (<a href="http://www.wikidata.org/entity/Q17145661">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q17157308">Star-shaped polymer</a> (<a href="http://www.wikidata.org/entity/Q17157308">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q18086822">Glycix</a> (<a href="http://www.wikidata.org/entity/Q18086822">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q18213341">conjugated polymer</a> (<a href="http://www.wikidata.org/entity/Q18213341">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q18392665">polyhexahydrotriazine</a> (<a href="http://www.wikidata.org/entity/Q18392665">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q18579463">Ethyl methyl cellulose</a> (<a href="http://www.wikidata.org/entity/Q18579463">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q21012207">sodium carboxy methyl cellulose</a> (<a href="http://www.wikidata.org/entity/Q21012207">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q21099595">Nylon 46</a> (<a href="http://www.wikidata.org/entity/Q21099595">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q22668726">lipegfilgrastim</a> (<a href="http://www.wikidata.org/entity/Q22668726">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q28936223">polyquaternium-7</a> (<a href="http://www.wikidata.org/entity/Q28936223">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q29550807">calcium lignosulfonate</a> (<a href="http://www.wikidata.org/entity/Q29550807">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q30688730">acetalated dextran</a> (<a href="http://www.wikidata.org/entity/Q30688730">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q43654570">cellulose acetate propionate</a> (<a href="http://www.wikidata.org/entity/Q43654570">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q46224534">10-formyltetrahydrofolyl polyglutamate</a> (<a href="http://www.wikidata.org/entity/Q46224534">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q48835766">promelacacinidin</a> (<a href="http://www.wikidata.org/entity/Q48835766">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q56313134">Q56313134</a> (<a href="http://www.wikidata.org/entity/Q56313134">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q72461886">Polyethylene glycol, chloromethyloxirane polymer</a> (<a href="http://www.wikidata.org/entity/Q72461886">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q72515319">carbomer</a> (<a href="http://www.wikidata.org/entity/Q72515319">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q74447161">polyethylene furandicarboxylate</a> (<a href="http://www.wikidata.org/entity/Q74447161">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q96400534">Pyrrole–imidazole polyamides</a> (<a href="http://www.wikidata.org/entity/Q96400534">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q96739808">sodium polystyrene sulfonate</a> (<a href="http://www.wikidata.org/entity/Q96739808">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q106958036">PG5</a> (<a href="http://www.wikidata.org/entity/Q106958036">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q111191732">polymer opals</a> (<a href="http://www.wikidata.org/entity/Q111191732">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q115174035">cured melamine resin</a> (<a href="http://www.wikidata.org/entity/Q115174035">edit</a>)</td>
  </tr>
  <tr>
    <td><a href="https://tools.wmflabs.org/scholia/Q117800634">Water-Soluble Synthetic Polymers</a> (<a href="http://www.wikidata.org/entity/Q117800634">edit</a>)</td>
  </tr>
</table>
## Code examples
### curl
```shell
curl -o polymersWithoutCXSMILES.rq https://raw.githubusercontent.com/egonw/SARS-CoV-2-Queries/master/sparql/polymersWithoutCXSMILES.rq
curl -H "Accept: text/tab-separated-values" -G https://query.wikidata.org/bigdata/namespace/wdq/sparql --data-urlencode query@polymersWithoutCXSMILES.rq
```
This SPARQL query is available under CCZero.
