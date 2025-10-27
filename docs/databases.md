# Comparing against databases

Wikidata uses the <a name="tp1">chemical graph</a> as important central criterion and with that the InChI and <a name="tp2">InChIKey</a>:
a different InChI basically means a different entry. However, because of phenomena like <a name="tp3">tautomerism</a>,
different Wikidata items can actually have the same InChI. But this makes the InChIKey also a powerful
tool to compare consistency with other <a name="tp4">databases</a>. The results of such a comparision is useful
input for manual curation efforts, e.g. when there is an inconsistency, it is not defined where
the cause of the inconsistency is.

This chapter covers example of these kind of checks.

## Common Chemistry

One systematic comparison that was performed was with the [CAS Common Chemistry](https://commonchemistry.cas.org/)
database [<a href="#citeref1">1</a>]. Using InChIKeys calculated from SMILES, records between <a name="tp5">CAS Common Chemistry</a>
and Wikidata were compared. If the chemical graph is the same (and thus the InChIKey), then the CAS registry
number in Wikidata should also match that in CAS Common Chemistry. Furthermore, because Wikidata has sitelinks
to Wikipedia, the paper also looked at CAS registry numbers in <a name="tp6">Wikipedia</a>. A similar effort was done for
checking CAS registry numbers in the <a name="tp7">HMDB</a> [<a href="#citeref2">2</a>]. The three scripts used to do these
analyses are provided in the supplementary information.

## References

1. <a name="citeref1"></a> Jacobs A, Williams D, Hickey K, Patrick N, Williams AJ, Chalk S, et al. CAS Common Chemistry in 2021: Expanding Access to Trusted Chemical Information for the Scientific Community. JCIM. 2022 May 13;  doi:[10.1021/ACS.JCIM.2C00268](https://doi.org/10.1021/ACS.JCIM.2C00268) ([Scholia](https://scholia.toolforge.org/doi/10.1021/ACS.JCIM.2C00268))
2. <a name="citeref2"></a> Wishart D, Guo A, Oler E, Wang F, Anjum A, Peters H, et al. HMDB 5.0: the Human Metabolome Database for 2022. NAR. 2022 Jan 1;50(D1):D622–31.  doi:[10.1093/NAR/GKAB1062](https://doi.org/10.1093/NAR/GKAB1062) ([Scholia](https://scholia.toolforge.org/doi/10.1093/NAR/GKAB1062))

