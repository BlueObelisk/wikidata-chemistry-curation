# Comparing against databases

Wikidata uses the <topic>chemical graph</topic> as important central criterion and with that the InChI and <topic>InChIKey</topic>:
a different InChI basically means a different entry. However, because of phenomena like <topic>tautomerism</topic>,
different Wikidata items can actually have the same InChI. But this makes the InChIKey also a powerful
tool to compare consistency with other <topic>databases</topic>. The results of such a comparision is useful
input for manual curation efforts, e.g. when there is an inconsistency, it is not defined where
the cause of the inconsistency is.

This chapter covers example of these kind of checks.
Most checks were performed using InChIKeys calculated from SMILES between records from the external database and Wikidata.
If the chemical graph is the same (and thus the InChIKey), then external identifiers in Wikidata should also match.

## Chemical Entities of Biological Interest (ChEBI)

ChEBI [<cite>Q902623</cite>] identifiers comparison was performed as described above.
The [ChEBI ID](https://www.wikidata.org/wiki/Property:P683) property also uses [mapping relation type](https://www.wikidata.org/wiki/Property:P4390) property as qualifier.
Most of the time, the matches are `exact match` [<cite>Q39893449</cite>].
<!-- TODO eventiually SPARQL to show statistics and other types of matches -->
The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_chebi_ids.R>

## Common Chemistry

One systematic comparison that was performed was with the [CAS Common Chemistry](https://commonchemistry.cas.org/) database [<cite>Q111987319</cite>].
<topic>CAS Common Chemistry</topic> and Wikidata were compared, because Wikidata has sitelinks
to <topic>Wikipedia</topic>, the paper also looked at CAS registry numbers in <topic>Wikipedia</topic>.
A similar effort was done for checking CAS registry numbers in the <topic>HMDB</topic> [<cite>Q112710355</cite>].
The three scripts used to do these analyses are provided in the supplementary information.

## DrugBank

TODO (I have it)

The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_drugbank_ids.R>

## DSSTox

TODO (I have it)

The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_dsstox_ids.R>

## HMDB

TODO (I have it)

The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_hmdb_ids.R>

## KNApSAcK

No open dump available

## nmrshiftdb2

No open dump available

## NP Atlas

TODO (I have it)

The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_npatlas_ids.R>

## PubChem

TODO (I have it)

The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_pubchem_ids.R>

## SureChEMBL

TODO (I have it)

The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_surechembl_ids.R>

## SwissLipids

TODO (I have it)

The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_swisslipids_ids.R>

## Unique Ingredient Identifier (UNII)

TODO (I have it)

The script used is available at <https://github.com/Adafede/wd-curation-r/inst/scripts/wd_add_unii_ids.R>

## References

<references/>
