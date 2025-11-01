# Adding additional information

This chapter describes various efforts that have taken place in the past to add content to Wikidata from
various (peer reviewed) sources. The serve as an example.

## Adding chemical compounds

The first 200 thousand chemical compounds were added in the work by Waagmeester, Stupp, Burgstaller-Muehlbacher, and others [<cite>Q87830400</cite>].
Willighagen wrote a CDK and Bacting based script to add chemical structures <!-- https://doi.org/10.59350/k8jnz-7fb76 -->, now
available as [Wikidata/createWDitemsFromSMILES.groovy](https://github.com/egonw/ons-wikidata/blob/main/Wikidata/createWDitemsFromSMILES.groovy).
This has been used to add many chemical compounds. By default, it only adds compounds with full stereochemistry defined.
It add the SMILES, InChI, InChIKey, and mass. If the InChIKey gives a match in PubChem, then the PubChem CID is added too.

## Melting points

Adding properties follow a similar process. If a SMILES is given, an InChIKey can be calculated, which can be used to
find the Wikidata items to which a property belongs. This has been used to add <topic>melting points</topic> from the
Jean-Claude Bradley Open Melting Point Dataset [<cite>Q69644056</cite>] using another Groovy script,
[MeltingPoints/createQuickStatements.groovy](https://github.com/egonw/ons-wikidata/blob/main/MeltingPoints/createQuickStatements.groovy).

## Boiling points

Earlier this year, another set of <topic>bioling points</topic> have been added, sourced from a 2004 article [<cite>Q51983889</cite>].
Yet another Groovy script, [BoilingPoints/createQuickStatements.groovy](https://github.com/egonw/ons-wikidata/blob/main/BoilingPoints/createQuickStatements.groovy), uses
[this gist](https://gist.github.com/dehaenw/9b43e42e17a388a4f66670d5f89e3378) as input to create QuickStatements.

## References

<references/>
