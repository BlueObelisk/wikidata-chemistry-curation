# Cheminformatics-based curation

## Chemistry Development Kit-based

Because SPARQL makes it very easy to extract data from Wikidata, it makes it easy to find
inconsistencies. For example, we can download all <topic>SMILES</topic> strings and parse the SMILES with
a library like the <topic>Chemistry Development Kit</topic> [<cite>Q30149558</cite>], for example,
using Bacting [<cite>Q107332190</cite>].

### Unparsable SMILES

Example code is avialable from
[checkSMILES.groovy](https://github.com/egonw/ons-wikidata/blob/main/Wikidata/checkSMILESes.groovy).
This script runs a SPARQL query to get all SMILES, and then tries to parse the string.
This will filter out many unparsable SMILES.

## RDkit-based

...

## References

<references/>
