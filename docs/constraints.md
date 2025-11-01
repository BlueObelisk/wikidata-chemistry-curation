# Wikidata property constraints

One way to keep control over the content of Wikidata is provided by Wikidata itself. These
are the <a name="tp1">property constraints</a>. For example, the property for the <a name="tp2">isomeric SMILES</a> requires
that each item in Wikidata has a different value (`distinct-values constraint`) and
can have only one (best) value (`single-best-value constraint`). Many properties also
use a regular expression to describe allowed values (`format constraint`).

Using these constraints, automated tests are routinely run resulting in reports. Not
all contraint violation, however, is a true error, and the mechanism does allow for
exceptions to be recorded. <!-- add example? --> For example, for the
<a name="tp3">MassBank accession ID</a>, format violations are reported, unique value violations, and more.

These reports provide both curators and users to get an idea of the status of the
chemistry in Wikidata.

For up-to-date information about properties used for chemicals: <https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry/Properties#Up-to-date_list_of_properties_about_chemical>

## Single value

Many external identifiers are expected to only be found on a single Wikidata items. This is particularly
the case when the external database uses the InChIKey has uniqueness criterion, like Wikidata.

All Wikidata properties have discussion pages that list constraint violations, and most of these
have matching SPARQL queries. For example, the <a name="tp4">ChEMBL ID</a> has this following SPARQL
query to find ChEMBL identifiers used on more than one Wikidata item:

**SPARQL** [sparql/P592UniqueValue.rq](sparql/P592UniqueValue.code.html) ([run](https://query.wikidata.org/embed.html#%23%20Unique%20value%20constraint%20report%20for%20P592%3A%20report%20by%20value%0A%0ASELECT%0A%20%20%20%20%3Fvalue%20%28SAMPLE%28%3Fct%29%20AS%20%3Fct%29%0A%20%20%20%20%28GROUP_CONCAT%28DISTINCT%28STRAFTER%28STR%28%3Fitem%29%2C%20%22%2Fentity%2F%22%29%29%3B%20separator%3D%22%2C%20%22%29%20AS%20%3Fitems%29%0A%20%20%20%20%28GROUP_CONCAT%28DISTINCT%28%3FitemLabel%29%3B%20separator%3D%22%2C%20%22%29%20AS%20%3Flabels%29%0AWHERE%0A%7B%0A%20%20%09%7B%20%09SELECT%20%3Fvalue%20%28COUNT%28DISTINCT%20%3Fitem%29%20as%20%3Fct%29%0A%20%20%09%09WHERE%0A%20%20%09%09%7B%0A%20%20%09%09%09%3Fitem%20wdt%3AP592%20%3Fvalue%0A%09%09%7D%0A%20%20%20%20%09GROUP%20BY%20%3Fvalue%20HAVING%20%28%3Fct%3E1%29%0A%20%20%20%20%09ORDER%20BY%20DESC%28%3Fct%29%0A%20%20%20%20%09LIMIT%20100%0A%09%7D%0A%20%20%09%3Fitem%20wdt%3AP592%20%3Fvalue%20.%0A%09SERVICE%20wikibase%3Alabel%20%7B%0A%20%20%20%20%09bd%3AserviceParam%20wikibase%3Alanguage%20%22en%2C%20mul%22%20.%0A%20%20%20%20%09%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%0A%20%20%09%7D%0A%7D%0AGROUP%20BY%20%3Fvalue%0AORDER%20BY%20DESC%28%3Fct%29%0A), [edit](https://query.wikidata.org/#%23%20Unique%20value%20constraint%20report%20for%20P592%3A%20report%20by%20value%0A%0ASELECT%0A%20%20%20%20%3Fvalue%20%28SAMPLE%28%3Fct%29%20AS%20%3Fct%29%0A%20%20%20%20%28GROUP_CONCAT%28DISTINCT%28STRAFTER%28STR%28%3Fitem%29%2C%20%22%2Fentity%2F%22%29%29%3B%20separator%3D%22%2C%20%22%29%20AS%20%3Fitems%29%0A%20%20%20%20%28GROUP_CONCAT%28DISTINCT%28%3FitemLabel%29%3B%20separator%3D%22%2C%20%22%29%20AS%20%3Flabels%29%0AWHERE%0A%7B%0A%20%20%09%7B%20%09SELECT%20%3Fvalue%20%28COUNT%28DISTINCT%20%3Fitem%29%20as%20%3Fct%29%0A%20%20%09%09WHERE%0A%20%20%09%09%7B%0A%20%20%09%09%09%3Fitem%20wdt%3AP592%20%3Fvalue%0A%09%09%7D%0A%20%20%20%20%09GROUP%20BY%20%3Fvalue%20HAVING%20%28%3Fct%3E1%29%0A%20%20%20%20%09ORDER%20BY%20DESC%28%3Fct%29%0A%20%20%20%20%09LIMIT%20100%0A%09%7D%0A%20%20%09%3Fitem%20wdt%3AP592%20%3Fvalue%20.%0A%09SERVICE%20wikibase%3Alabel%20%7B%0A%20%20%20%20%09bd%3AserviceParam%20wikibase%3Alanguage%20%22en%2C%20mul%22%20.%0A%20%20%20%20%09%3Fitem%20rdfs%3Alabel%20%3FitemLabel%20.%0A%20%20%09%7D%0A%7D%0AGROUP%20BY%20%3Fvalue%0AORDER%20BY%20DESC%28%3Fct%29%0A))

```sparql
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

While this query shows a few false positives caused by tautomerism, it provides a useful
list to regularly check:

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
  <tr><td colspan="2"><a href="sparql/P592UniqueValue.code.html">sparql/P592UniqueValue.rq</a></td></tr>
</table>

## Uniqe value

Smilarly, we can use SPARQL to find Wikidata items with more than one ChEMBL identifier:

**SPARQL** [sparql/P592SingleValue.rq](sparql/P592SingleValue.code.html) ([run](https://query.wikidata.org/embed.html#SELECT%20DISTINCT%20%3FitemLabel%20%3FitemLabelURL%20%3Fcount%20%3Fsample1%20%3Fsample2%20%3Fexception%0AWITH%20%7B%0A%09SELECT%20%3Fformatter%20WHERE%20%7B%0A%09%09OPTIONAL%20%7B%20wd%3AP592%20wdt%3AP1630%20%3Fformatter%20%7D%0A%09%7D%20LIMIT%201%0A%7D%20AS%20%25formatter%0AWHERE%0A%7B%0A%09%7B%0A%09%09SELECT%20%3Fitem%20%28COUNT%28%3Fvalue%29%20AS%20%3Fcount%29%20%28MIN%28%3Fvalue%29%20AS%20%3Fsample1%29%20%28MAX%28%3Fvalue%29%20AS%20%3Fsample2%29%20%7B%0A%09%09%09%3Fitem%20p%3AP592%20%5B%20ps%3AP592%20%3Fval%3B%20wikibase%3Arank%20%3Frank%20%5D%20.%0A%09%09%09FILTER%28%20%3Frank%20%21%3D%20wikibase%3ADeprecatedRank%20%29%20.%0A%09%09%09INCLUDE%20%25formatter%20.%0A%09%09%09BIND%28%20IF%28%20BOUND%28%20%3Fformatter%20%29%2C%20URI%28%20REPLACE%28%20%3Fformatter%2C%20%27%5C%5C%241%27%2C%20%3Fval%20%29%20%29%2C%20%3Fval%20%29%20AS%20%3Fvalue%20%29%20.%0A%09%09%7D%20GROUP%20BY%20%3Fitem%20HAVING%20%28%20%3Fcount%20%3E%201%20%29%20LIMIT%20100%0A%09%7D%20.%0A%09OPTIONAL%20%7B%0A%09%09wd%3AP592%20p%3AP2302%20%5B%20ps%3AP2302%20wd%3AQ19474404%3B%20pq%3AP2303%20%3Fexc%20%5D%20.%0A%09%09FILTER%28%20%3Fexc%20%3D%20%3Fitem%20%29%20.%0A%09%7D%20.%0A%09BIND%28%20BOUND%28%20%3Fexc%20%29%20AS%20%3Fexception%20%29%20.%0A%20%20%20%20BIND%20%28%3Fitem%20AS%20%3FitemLabelURL%29%0A%09SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%2Cmul%22%20%7D%20.%0A%7D%0AORDER%20BY%20DESC%28%3Fcount%29%0A), [edit](https://query.wikidata.org/#SELECT%20DISTINCT%20%3FitemLabel%20%3FitemLabelURL%20%3Fcount%20%3Fsample1%20%3Fsample2%20%3Fexception%0AWITH%20%7B%0A%09SELECT%20%3Fformatter%20WHERE%20%7B%0A%09%09OPTIONAL%20%7B%20wd%3AP592%20wdt%3AP1630%20%3Fformatter%20%7D%0A%09%7D%20LIMIT%201%0A%7D%20AS%20%25formatter%0AWHERE%0A%7B%0A%09%7B%0A%09%09SELECT%20%3Fitem%20%28COUNT%28%3Fvalue%29%20AS%20%3Fcount%29%20%28MIN%28%3Fvalue%29%20AS%20%3Fsample1%29%20%28MAX%28%3Fvalue%29%20AS%20%3Fsample2%29%20%7B%0A%09%09%09%3Fitem%20p%3AP592%20%5B%20ps%3AP592%20%3Fval%3B%20wikibase%3Arank%20%3Frank%20%5D%20.%0A%09%09%09FILTER%28%20%3Frank%20%21%3D%20wikibase%3ADeprecatedRank%20%29%20.%0A%09%09%09INCLUDE%20%25formatter%20.%0A%09%09%09BIND%28%20IF%28%20BOUND%28%20%3Fformatter%20%29%2C%20URI%28%20REPLACE%28%20%3Fformatter%2C%20%27%5C%5C%241%27%2C%20%3Fval%20%29%20%29%2C%20%3Fval%20%29%20AS%20%3Fvalue%20%29%20.%0A%09%09%7D%20GROUP%20BY%20%3Fitem%20HAVING%20%28%20%3Fcount%20%3E%201%20%29%20LIMIT%20100%0A%09%7D%20.%0A%09OPTIONAL%20%7B%0A%09%09wd%3AP592%20p%3AP2302%20%5B%20ps%3AP2302%20wd%3AQ19474404%3B%20pq%3AP2303%20%3Fexc%20%5D%20.%0A%09%09FILTER%28%20%3Fexc%20%3D%20%3Fitem%20%29%20.%0A%09%7D%20.%0A%09BIND%28%20BOUND%28%20%3Fexc%20%29%20AS%20%3Fexception%20%29%20.%0A%20%20%20%20BIND%20%28%3Fitem%20AS%20%3FitemLabelURL%29%0A%09SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22en%2Cmul%22%20%7D%20.%0A%7D%0AORDER%20BY%20DESC%28%3Fcount%29%0A))

```sparql
SELECT DISTINCT ?itemLabel ?itemLabelURL ?count ?sample1 ?sample2 ?exception
WITH {
	SELECT ?formatter WHERE {
		OPTIONAL { wd:P592 wdt:P1630 ?formatter }
	} LIMIT 1
} AS %formatter
WHERE
{
	{
		SELECT ?item (COUNT(?value) AS ?count) (MIN(?value) AS ?sample1) (MAX(?value) AS ?sample2) {
			?item p:P592 [ ps:P592 ?val; wikibase:rank ?rank ] .
			FILTER( ?rank != wikibase:DeprecatedRank ) .
			INCLUDE %formatter .
			BIND( IF( BOUND( ?formatter ), URI( REPLACE( ?formatter, '\\$1', ?val ) ), ?val ) AS ?value ) .
		} GROUP BY ?item HAVING ( ?count > 1 ) LIMIT 100
	} .
	OPTIONAL {
		wd:P592 p:P2302 [ ps:P2302 wd:Q19474404; pq:P2303 ?exc ] .
		FILTER( ?exc = ?item ) .
	} .
	BIND( BOUND( ?exc ) AS ?exception ) .
    BIND (?item AS ?itemLabelURL)
	SERVICE wikibase:label { bd:serviceParam wikibase:language "en,mul" } .
}
ORDER BY DESC(?count)
```

This gives this list of Wikidata items with more than one ChEMBL ID:

<table>
  <tr>
    <td><b>itemLabelURL</b></td>
    <td><b>count</b></td>
    <td><b>sample1</b></td>
    <td><b>sample2</b></td>
    <td><b>exception</b></td>
  </tr>
  <tr>
    <td>http://www.wikidata.org/entity/Q425293</td>
    <td>2</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL3039598/</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL3306578/</td>
    <td>false</td>
  </tr>
  <tr>
    <td>http://www.wikidata.org/entity/Q4008670</td>
    <td>2</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL2103975/</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL264186/</td>
    <td>false</td>
  </tr>
  <tr>
    <td>http://www.wikidata.org/entity/Q417219</td>
    <td>2</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL2079587/</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL3182301/</td>
    <td>false</td>
  </tr>
  <tr>
    <td>http://www.wikidata.org/entity/Q75830</td>
    <td>2</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL18041/</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL28992/</td>
    <td>false</td>
  </tr>
  <tr>
    <td>http://www.wikidata.org/entity/Q422301</td>
    <td>2</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL1201488/</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL3039582/</td>
    <td>false</td>
  </tr>
  <tr>
    <td>http://www.wikidata.org/entity/Q420532</td>
    <td>2</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL3039593/</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL553025/</td>
    <td>false</td>
  </tr>
  <tr>
    <td>http://www.wikidata.org/entity/Q7784695</td>
    <td>2</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL10247/</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL298827/</td>
    <td>false</td>
  </tr>
  <tr>
    <td>http://www.wikidata.org/entity/Q417227</td>
    <td>2</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL1286/</td>
    <td>https://www.ebi.ac.uk/chembl/compound_report_card/CHEMBL150361/</td>
    <td>false</td>
  </tr>
  <tr><td colspan="2"><a href="sparql/P592SingleValue.code.html">sparql/P592SingleValue.rq</a></td></tr>
</table>

## References


