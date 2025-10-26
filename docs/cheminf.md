# Cheminformatics-based curation

## Chemistry Development Kit-based

Because SPARQL makes it very easy to extract data from Wikidata, it makes it easy to find
inconsistencies. For example, we can download all <a name="tp1">SMILES</a> strings and parse the SMILES with
a library like the <a name="tp2">Chemistry Development Kit</a> [<a href="#citeref1">1</a>], for example,
using Bacting [<a href="#citeref2">2</a>].

### Unparsable SMILES

Example code is avialable from
[checkSMILES.groovy](https://github.com/egonw/ons-wikidata/blob/main/Wikidata/checkSMILESes.groovy).
This script runs a SPARQL query to get all SMILES, and then tries to parse the string.
This will filter out many unparsable SMILES.

## RDkit-based

...

## References

1. <a name="citeref1"></a> Willighagen E, Mayfield JW, Alvarsson J, Berg A, Carlsson L, Jeliazkova N, et al. The Chemistry Development Kit (CDK) v2.0: atom typing, depiction, molecular formulas, and substructure searching. J Cheminform. 2017 Jun 6;9(1).  doi:[10.1186/S13321-017-0220-4](https://doi.org/10.1186/S13321-017-0220-4) ([Scholia](https://scholia.toolforge.org/doi/10.1186/S13321-017-0220-4))
2. <a name="citeref2"></a> Willighagen E. Bacting: a next generation, command line version of Bioclipse. JOSS. 2021 Jun 23;6(62):2558.  doi:[10.21105/JOSS.02558](https://doi.org/10.21105/JOSS.02558) ([Scholia](https://scholia.toolforge.org/doi/10.21105/JOSS.02558))

