# functionalGroupsWithoutCXSMILES.rq
**Code examples:** [curl](#curl)
### SPARQL
```sparql
SELECT ?fg ?fgLabel ?cxsmiles WHERE {
  ?fg wdt:P31/wdt:P279* wd:Q170409 .
  MINUS { ?fg wdt:P10718 ?cxsmiles }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],mul,en". }
}
```
[Execute](https://query.wikidata.org/embed.html#SELECT%20%3Ffg%20%3FfgLabel%20%3Fcxsmiles%20WHERE%20%7B%0A%20%20%3Ffg%20wdt%3AP31%2Fwdt%3AP279*%20wd%3AQ170409%20.%0A%20%20MINUS%20%7B%20%3Ffg%20wdt%3AP10718%20%3Fcxsmiles%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cmul%2Cen%22.%20%7D%0A%7D%0A) or [Edit](https://query.wikidata.org/#SELECT%20%3Ffg%20%3FfgLabel%20%3Fcxsmiles%20WHERE%20%7B%0A%20%20%3Ffg%20wdt%3AP31%2Fwdt%3AP279*%20wd%3AQ170409%20.%0A%20%20MINUS%20%7B%20%3Ffg%20wdt%3AP10718%20%3Fcxsmiles%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cmul%2Cen%22.%20%7D%0A%7D%0A)


### Output
<table>
  <tr>
    <td><b>fg</b></td>
    <td><b>cxsmiles</b></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q2633793">acetamido group</a> (<a href="http://www.wikidata.org/entity/Q2633793">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q2633806">peroxyacetyl group</a> (<a href="http://www.wikidata.org/entity/Q2633806">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q2896782">benzhydryl</a> (<a href="http://www.wikidata.org/entity/Q2896782">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q2972820">cinnamyl group</a> (<a href="http://www.wikidata.org/entity/Q2972820">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q3097695">cumyl group</a> (<a href="http://www.wikidata.org/entity/Q3097695">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q3382145">phenethyl group</a> (<a href="http://www.wikidata.org/entity/Q3382145">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q3501377">styryl group</a> (<a href="http://www.wikidata.org/entity/Q3501377">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q3535942">dodecyl group</a> (<a href="http://www.wikidata.org/entity/Q3535942">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q5198967">cyclopropyl group</a> (<a href="http://www.wikidata.org/entity/Q5198967">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q7485453">methylene group</a> (<a href="http://www.wikidata.org/entity/Q7485453">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q7932951">vinylene group</a> (<a href="http://www.wikidata.org/entity/Q7932951">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q7932953">vinylidene group</a> (<a href="http://www.wikidata.org/entity/Q7932953">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q9281428">isocyanide group</a> (<a href="http://www.wikidata.org/entity/Q9281428">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q11186406">2-methoxyethoxymethyl group</a> (<a href="http://www.wikidata.org/entity/Q11186406">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q11186405">2-(Trimethylsilyl)ethoxymethyl</a> (<a href="http://www.wikidata.org/entity/Q11186405">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q11319313">Q11319313</a> (<a href="http://www.wikidata.org/entity/Q11319313">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q11343884">Q11343884</a> (<a href="http://www.wikidata.org/entity/Q11343884">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q11702621">aldehyde group</a> (<a href="http://www.wikidata.org/entity/Q11702621">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q12028098">carboxymethyl</a> (<a href="http://www.wikidata.org/entity/Q12028098">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q13724862">Heptyl group</a> (<a href="http://www.wikidata.org/entity/Q13724862">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q13726482">hexyl group</a> (<a href="http://www.wikidata.org/entity/Q13726482">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q24890263">Q24890263</a> (<a href="http://www.wikidata.org/entity/Q24890263">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q28458054">cyanomethyl group</a> (<a href="http://www.wikidata.org/entity/Q28458054">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q29175676">2,4-dinitrophenyl group</a> (<a href="http://www.wikidata.org/entity/Q29175676">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q33776806">aminobenzal</a> (<a href="http://www.wikidata.org/entity/Q33776806">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q55643432">trichloromethyl</a> (<a href="http://www.wikidata.org/entity/Q55643432">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q56425361">sec-butyl group</a> (<a href="http://www.wikidata.org/entity/Q56425361">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q56425371">isobutyl</a> (<a href="http://www.wikidata.org/entity/Q56425371">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q56427316">mesyl group</a> (<a href="http://www.wikidata.org/entity/Q56427316">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q56427316">mesyl group</a> (<a href="http://www.wikidata.org/entity/Q56427316">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q56823124">1-Propynyl group</a> (<a href="http://www.wikidata.org/entity/Q56823124">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q56824847">methanetriyl group</a> (<a href="http://www.wikidata.org/entity/Q56824847">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q56824877">methanylylidene group</a> (<a href="http://www.wikidata.org/entity/Q56824877">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q57708398">azanediyl group</a> (<a href="http://www.wikidata.org/entity/Q57708398">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q57708604">azanylylidene group</a> (<a href="http://www.wikidata.org/entity/Q57708604">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q57708714">azanylidyne group</a> (<a href="http://www.wikidata.org/entity/Q57708714">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q57712202">nitroso group</a> (<a href="http://www.wikidata.org/entity/Q57712202">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q58261337">L-tyrosyl group</a> (<a href="http://www.wikidata.org/entity/Q58261337">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q58261436">D-tyrosyl group</a> (<a href="http://www.wikidata.org/entity/Q58261436">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q62021566">aminomethyl group</a> (<a href="http://www.wikidata.org/entity/Q62021566">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q64706146">ethene-1,1-diyl group</a> (<a href="http://www.wikidata.org/entity/Q64706146">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q76592161">propionyl</a> (<a href="http://www.wikidata.org/entity/Q76592161">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q86214874">methylidene group</a> (<a href="http://www.wikidata.org/entity/Q86214874">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q91783710">phenoxy group</a> (<a href="http://www.wikidata.org/entity/Q91783710">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q107522077">hexadecyl</a> (<a href="http://www.wikidata.org/entity/Q107522077">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q112061576">Dimethoxytrityl</a> (<a href="http://www.wikidata.org/entity/Q112061576">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q112967652">Electron-withdrawing group</a> (<a href="http://www.wikidata.org/entity/Q112967652">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q113499788">azinoyl group</a> (<a href="http://www.wikidata.org/entity/Q113499788">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q115685481">carbonate group</a> (<a href="http://www.wikidata.org/entity/Q115685481">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q115869943">chloryl group</a> (<a href="http://www.wikidata.org/entity/Q115869943">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q115869943">chloryl group</a> (<a href="http://www.wikidata.org/entity/Q115869943">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q116889985">diazo group</a> (<a href="http://www.wikidata.org/entity/Q116889985">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q117226948">thioketone group</a> (<a href="http://www.wikidata.org/entity/Q117226948">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q117226962">thioaldehyde group</a> (<a href="http://www.wikidata.org/entity/Q117226962">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q123226598">perchloryl group</a> (<a href="http://www.wikidata.org/entity/Q123226598">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q123226598">perchloryl group</a> (<a href="http://www.wikidata.org/entity/Q123226598">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q125823083">ketene group</a> (<a href="http://www.wikidata.org/entity/Q125823083">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q127256072">hydroperoxyl group</a> (<a href="http://www.wikidata.org/entity/Q127256072">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q127600641">Octyl group</a> (<a href="http://www.wikidata.org/entity/Q127600641">edit</a>)</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="https://scholia.toolforge.org/Q131785069">Q131785069</a> (<a href="http://www.wikidata.org/entity/Q131785069">edit</a>)</td>
    <td></td>
  </tr>
</table>
## Code examples
### curl
```shell
curl -o functionalGroupsWithoutCXSMILES.rq https://raw.githubusercontent.com/egonw/SARS-CoV-2-Queries/master/sparql/functionalGroupsWithoutCXSMILES.rq
curl -H "Accept: text/tab-separated-values" -G https://query.wikidata.org/bigdata/namespace/wdq/sparql --data-urlencode query@functionalGroupsWithoutCXSMILES.rq
```
This SPARQL query is available under CCZero.
