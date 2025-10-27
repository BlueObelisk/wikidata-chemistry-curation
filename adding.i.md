# Adding additional information

## Adding chemical compounds

The first 200 thousand chemical compounds were added in the work by Waagmeester, Stupp, Burgstaller-Muehlbacher, and others [<cite>Q87830400</cite>].
Willighagen wrote a CDK and Bacting based script to add chemical structures <!-- https://doi.org/10.59350/k8jnz-7fb76 -->, now
available as [createWDitemsFromSMILES.groovy](https://github.com/egonw/ons-wikidata/blob/main/Wikidata/createWDitemsFromSMILES.groovy).
This has been used to add many chemical compounds. By default, it only adds compounds with full stereochemistry defined.
It add the SMILES, InChI, InChIKey, and mass. If the InChIKey gives a match in PubChem, then the PubChem CID is added too.

## Adding melting points


