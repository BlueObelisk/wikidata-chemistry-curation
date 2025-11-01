# P592UniqueValue.rq
**Code examples:** [curl](#curl)
### SPARQL
```sparql
# Unique value constraint report for P592: report by value

SELECT
    ?value (SAMPLE(?ct) AS ?ct)
    (GROUP_CONCAT(DISTINCT(STRAFTER(STR(?item), "/entity/")); separator=", ") AS ?items)
    (GROUP_CONCAT(DISTINCT(?itemLabel); separator=", ") AS ?labels)
WHERE
{
  	{ 	SELECT ?value (COUNT(DISTINCT ?item) as ?ct)
  		WHERE
  		{
  			?item wdt:P592 ?value
		}
    	GROUP BY ?value HAVING (?ct>1)
    	ORDER BY DESC(?ct)
    	LIMIT 100
	}
  	?item wdt:P592 ?value .
	SERVICE wikibase:label {
    	bd:serviceParam wikibase:language "en, mul" .
    	?item rdfs:label ?itemLabel .
  	}
}
GROUP BY ?value
ORDER BY DESC(?ct)
```
[Execute](https://query.wikidata.org/embed.html#%23%20Unique%20value%20constraint%20report%20for%20P592%3A%20report%20by%20value%0A%0ASELECT%0A%20%20%20%20%3Fvalue%20%28SAMPLE%28%3Fct%29%20AS%20%3Fct%29%0A%20%20%20%20%28GROUP_CONCAT%28DISTINCT%28STRAFTER%28STR%28%3Fitem%29%2C%20%22%2Fentity%2F%22%29%29%3B%20separator%3D%22%2C%20%22%29%20AS%20%3Fitems%29%0A%20%20%20%20%28GROUP_CONCAT%28DISTINCT%28%3FitemLabel%29%3B%20separator%3D%22%2C%20%22%29%20AS%20%3Flabels%29%0AWHERE%0A%7B%0A%20%20%09%7B%20%09SELECT%20%3Fvalue%20%28COUNT%28DISTINCT%20%3Fitem%29%20as%20%3Fct%29%0A%20%20%09%09WHERE%0A%20%20%09%09%7B%0A%20%20%09%09%09%3Fitem%20wdt%3AP592%20%3Fvalue%0A%09%09%7D%0A%20%20%20%20%09GROUP%20BY%20%3Fvalue%20HAVING%20%28%3Fct%3E1%29%0A%20%20%20%20%09ORDER%20BY%20DESC%28%3Fct%29%0A%20%20%20%20%09LIMIT%20100%0A%09%7D%0A%20%20%09%3Fitem%20wdt%3AP592%20%3Fvalue%20.%0A%09SERVICE%20wikibase%3Alabel%20%7B%0A%20%20%20%20%09bd%3AserviceParam%20wikibase%3Alanguage%20%22en%2C%20mul%22%20.%0A%20%20%20%20%09%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%0A%20%20%09%7D%0A%7D%0AGROUP%20BY%20%3Fvalue%0AORDER%20BY%20DESC%28%3Fct%29%0A) or [Edit](https://query.wikidata.org/#%23%20Unique%20value%20constraint%20report%20for%20P592%3A%20report%20by%20value%0A%0ASELECT%0A%20%20%20%20%3Fvalue%20%28SAMPLE%28%3Fct%29%20AS%20%3Fct%29%0A%20%20%20%20%28GROUP_CONCAT%28DISTINCT%28STRAFTER%28STR%28%3Fitem%29%2C%20%22%2Fentity%2F%22%29%29%3B%20separator%3D%22%2C%20%22%29%20AS%20%3Fitems%29%0A%20%20%20%20%28GROUP_CONCAT%28DISTINCT%28%3FitemLabel%29%3B%20separator%3D%22%2C%20%22%29%20AS%20%3Flabels%29%0AWHERE%0A%7B%0A%20%20%09%7B%20%09SELECT%20%3Fvalue%20%28COUNT%28DISTINCT%20%3Fitem%29%20as%20%3Fct%29%0A%20%20%09%09WHERE%0A%20%20%09%09%7B%0A%20%20%09%09%09%3Fitem%20wdt%3AP592%20%3Fvalue%0A%09%09%7D%0A%20%20%20%20%09GROUP%20BY%20%3Fvalue%20HAVING%20%28%3Fct%3E1%29%0A%20%20%20%20%09ORDER%20BY%20DESC%28%3Fct%29%0A%20%20%20%20%09LIMIT%20100%0A%09%7D%0A%20%20%09%3Fitem%20wdt%3AP592%20%3Fvalue%20.%0A%09SERVICE%20wikibase%3Alabel%20%7B%0A%20%20%20%20%09bd%3AserviceParam%20wikibase%3Alanguage%20%22en%2C%20mul%22%20.%0A%20%20%20%20%09%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%0A%20%20%09%7D%0A%7D%0AGROUP%20BY%20%3Fvalue%0AORDER%20BY%20DESC%28%3Fct%29%0A)


### Output
<table>
  <tr>
    <td><b>value</b></td>
    <td><b>ct</b></td>
    <td><b>items</b></td>
    <td><b>labels</b></td>
  </tr>
  <tr>
    <td>CHEMBL521177</td>
    <td>2</td>
    <td>Q6469057, Q105287434</td>
    <td>lactucin, 4-epi-lactucin</td>
  </tr>
  <tr>
    <td>CHEMBL1206440</td>
    <td>2</td>
    <td>Q2130929, Q27124801</td>
    <td>cyclamic acid, cyclamate</td>
  </tr>
  <tr>
    <td>CHEMBL2303614</td>
    <td>2</td>
    <td>Q408014, Q74511001</td>
    <td>chondroitin sulfate, (2S,3S,4S,5R,6S)-6-[[(2R,3R,4S,5R,6S)-3-Acetamido-2,6-bis(hydroxymethyl)-5-(sulfomethyl)oxan-4-yl]methoxymethyl]-4,5-dihydroxy-3-(hydroxymethyl)oxane-2-carboxylic acid</td>
  </tr>
  <tr>
    <td>CHEMBL1433</td>
    <td>2</td>
    <td>Q422442, Q82982262</td>
    <td>doxycycline, doxycycline tautomer</td>
  </tr>
  <tr>
    <td>CHEMBL91</td>
    <td>2</td>
    <td>Q410534, Q75163056</td>
    <td>miconazole, rac-miconazole</td>
  </tr>
  <tr>
    <td>CHEMBL1201341</td>
    <td>2</td>
    <td>Q4352952, Q27077150</td>
    <td>echothiophate</td>
  </tr>
  <tr>
    <td>CHEMBL1201668</td>
    <td>2</td>
    <td>Q6997373, Q66360952</td>
    <td>nesiritide, brain natriuretic peptide</td>
  </tr>
  <tr>
    <td>CHEMBL2110884</td>
    <td>2</td>
    <td>Q27284343, Q76005793</td>
    <td>cetocycline, cetocycline tautomer</td>
  </tr>
  <tr>
    <td>CHEMBL1685065</td>
    <td>2</td>
    <td>Q27157614, Q82124319</td>
    <td>1,2-dihexadecanoyl-sn-glycero-3-phospho-(1D-myo-inositol-3,4,5-trisphosphate)</td>
  </tr>
  <tr>
    <td>CHEMBL1591</td>
    <td>2</td>
    <td>Q2736402, Q76728423</td>
    <td>demeclocycline, (4S,4aS,5aS,6S,12aR)-7-chloro-4-(dimethylamino)-1,6,10,11,12a-pentahydroxy-3,12-dioxo-4a,5,5a,6-tetrahydro-4H-tetracene-2-carboxamide</td>
  </tr>
  <tr>
    <td>CHEMBL1233322</td>
    <td>2</td>
    <td>Q27093187, Q106570944</td>
    <td>2-amino-6-(hydroxymethyl)-7,8-dihydropteridin-4-ol, 6-Hydroxymethyl-7,8-dihydropterin</td>
  </tr>
  <tr>
    <td>CHEMBL2008411</td>
    <td>2</td>
    <td>Q5629606, Q112931028</td>
    <td>HHTDD, hexaazatricyclododecanedione</td>
  </tr>
  <tr>
    <td>CHEMBL435170</td>
    <td>2</td>
    <td>Q4680659, Q113940477</td>
    <td>adaprolol, deucravacitinib</td>
  </tr>
  <tr>
    <td>CHEMBL268697</td>
    <td>2</td>
    <td>Q15409437, Q82913190</td>
    <td>hemicholinium-3 dibromide, 2,2'-([1,1'-Biphenyl]-4,4'-diyl)bis(2-hydroxy-4,4-dimethylmorpholin-4-ium)</td>
  </tr>
  <tr>
    <td>CHEMBL1201414</td>
    <td>2</td>
    <td>Q411198, Q20817252</td>
    <td>tinzaparin sodium, tinzaparin</td>
  </tr>
</table>
## Code examples
### curl
```shell
curl -o P592UniqueValue.rq https://raw.githubusercontent.com/egonw/SARS-CoV-2-Queries/master/sparql/P592UniqueValue.rq
curl -H "Accept: text/tab-separated-values" -G https://query.wikidata.org/bigdata/namespace/wdq/sparql --data-urlencode query@P592UniqueValue.rq
```
This SPARQL query is available under CCZero.
