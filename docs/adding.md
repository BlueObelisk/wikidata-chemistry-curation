# Adding additional information

This chapter describes various efforts that have taken place in the past to add content to Wikidata from
various (peer reviewed) sources. The serve as an example.

## Adding chemical compounds

The first 200 thousand chemical compounds were added in the work by Waagmeester, Stupp, Burgstaller-Muehlbacher, and others [<a href="#citeref1">1</a>].
Willighagen wrote a CDK and Bacting based script to add chemical structures <!-- https://doi.org/10.59350/k8jnz-7fb76 -->, now
available as [Wikidata/createWDitemsFromSMILES.groovy](https://github.com/egonw/ons-wikidata/blob/main/Wikidata/createWDitemsFromSMILES.groovy).
This has been used to add many chemical compounds. By default, it only adds compounds with full stereochemistry defined.
It add the SMILES, InChI, InChIKey, and mass. If the InChIKey gives a match in PubChem, then the PubChem CID is added too.

## Melting points

Adding properties follow a similar process. If a SMILES is given, an InChIKey can be calculated, which can be used to
find the Wikidata items to which a property belongs. This has been used to add <a name="tp1">melting points</a> from the
Jean-Claude Bradley Open Melting Point Dataset [<a href="#citeref2">2</a>] using another Groovy script,
[MeltingPoints/createQuickStatements.groovy](https://github.com/egonw/ons-wikidata/blob/main/MeltingPoints/createQuickStatements.groovy).

## Boiling points

Earlier this year, another set of <a name="tp2">bioling points</a> have been added, sourced from a 2004 article [<a href="#citeref3">3</a>].
Yet another Groovy script, [BoilingPoints/createQuickStatements.groovy](https://github.com/egonw/ons-wikidata/blob/main/BoilingPoints/createQuickStatements.groovy), uses
[this gist](https://gist.github.com/dehaenw/9b43e42e17a388a4f66670d5f89e3378) as input to create QuickStatements.

## References

1. <a name="citeref1"></a> Waagmeester A, Stupp G, Burgstaller-Muehlbacher S, Good BM, Griffith M, Griffith O, et al. Wikidata as a knowledge graph for the life sciences. eLife [Internet]. 2020 Mar 17;9. Available from: https://elifesciences.org/articles/52614 doi:[10.7554/ELIFE.52614](https://doi.org/10.7554/ELIFE.52614) ([Scholia](https://scholia.toolforge.org/doi/10.7554/ELIFE.52614))
2. <a name="citeref2"></a> Bradley JC, Williams AJ, Lang ASID. Jean-Claude Bradley Open Melting Point Dataset [Internet]. Figshare. 2014. Available from: https://figshare.com/articles/Jean_Claude_Bradley_Open_Melting_Point_Datset/1031637/2 doi:[10.6084/M9.FIGSHARE.1031637.V2](https://doi.org/10.6084/M9.FIGSHARE.1031637.V2) ([Scholia](https://scholia.toolforge.org/doi/10.6084/M9.FIGSHARE.1031637.V2))
3. <a name="citeref3"></a> Rücker C, Meringer M, Kerber A. QSPR using MOLGEN-QSPR: the example of haloalkane boiling points. JCICS. 2004 Nov 1;44(6):2070–6.  doi:[10.1021/CI049802U](https://doi.org/10.1021/CI049802U) ([Scholia](https://scholia.toolforge.org/doi/10.1021/CI049802U))

