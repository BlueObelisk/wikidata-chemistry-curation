# Comparing against databases

Wikidata uses the <a name="tp1">chemical graph</a> as important central criterion and with that the InChI and <a name="tp2">InChIKey</a>:
a different InChI basically means a different entry. However, because of phenomena like <a name="tp3">tautomerism</a>,
different Wikidata items can actually have the same InChI. But this makes the InChIKey also a powerful
tool to compare consistency with other <a name="tp4">databases</a>. The results of such a comparision is useful
input for manual curation efforts, e.g. when there is an inconsistency, it is not defined where
the cause of the inconsistency is.

This chapter covers example of these kind of checks.
Most checks were performed using InChIKeys calculated from SMILES between records from the external database and Wikidata.
If the chemical graph is the same (and thus the InChIKey), then external identifiers in Wikidata should also match.

## Chemical Entities of Biological Interest (ChEBI)

ChEBI [<a href="#citeref1">1</a>] identifiers comparison was performed as described above, based on InChIs, not InChIKeys.
The [ChEBI ID](https://www.wikidata.org/wiki/Property:P683) property also uses [mapping relation type](https://www.wikidata.org/wiki/Property:P4390) property as qualifier.
Most of the time, the matches are `exact match` [<a href="#citeref2">2</a>].
<!-- TODO eventiually SPARQL to show statistics and other types of matches -->
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_chebi_ids.R>

## Common Chemistry

One systematic comparison that was performed was with the [CAS Common Chemistry](https://commonchemistry.cas.org/) database [<a href="#citeref3">3</a>].
<a name="tp5">CAS Common Chemistry</a> and Wikidata were compared, because Wikidata has sitelinks
to <a name="tp6">Wikipedia</a>, the paper also looked at CAS registry numbers in <a name="tp7">Wikipedia</a>.
A similar effort was done for checking CAS registry numbers in the <a name="tp8">HMDB</a> [<a href="#citeref4">4</a>].
The three scripts used to do these analyses are provided in the supplementary information.

## DrugBank

The same methodology as described above was used.
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_drugbank_ids.R>

## DSSTox

The same methodology as described above was used.
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_dsstox_ids.R>

## HMDB

The same methodology as described above was used.
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_hmdb_ids.R>

## KNApSAcK

No open dump available

## nmrshiftdb2

No open dump available

## NP Atlas

The same methodology as described above was used.
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_npatlas_ids.R>

## PubChem

The same methodology as described above was used.
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_pubchem_ids.R>

## SureChEMBL

The same methodology as described above was used.
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_surechembl_ids.R>

## SwissLipids

The same methodology as described above was used.
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_swisslipids_ids.R>

## Unique Ingredient Identifier (UNII)

The same methodology as described above was used.
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_unii_ids.R>

## References

1. <a name="citeref1"></a>Missing
2. <a name="citeref2"></a>Missing
3. <a name="citeref3"></a> Jacobs A, Williams D, Hickey K, Patrick N, Williams AJ, Chalk S, et al. CAS Common Chemistry in 2021: Expanding Access to Trusted Chemical Information for the Scientific Community. JCIM. 2022 May 13;  doi:[10.1021/ACS.JCIM.2C00268](https://doi.org/10.1021/ACS.JCIM.2C00268) ([Scholia](https://scholia.toolforge.org/doi/10.1021/ACS.JCIM.2C00268))
4. <a name="citeref4"></a> Wishart D, Guo A, Oler E, Wang F, Anjum A, Peters H, et al. HMDB 5.0: the Human Metabolome Database for 2022. NAR. 2022 Jan 1;50(D1):D622–31.  doi:[10.1093/NAR/GKAB1062](https://doi.org/10.1093/NAR/GKAB1062) ([Scholia](https://scholia.toolforge.org/doi/10.1093/NAR/GKAB1062))

