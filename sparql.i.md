# Wikidata-based curation approaches

## Wikidata items without SMILES

Wikipedia has a separate chemistry community, and while some Wikidata chemistry content is visible on
<topic>Wikipedia</topic>, it also happens regularly that Wikipedia has a <topic>SMILES</topic> for a chemical compound, where Wikidata
does not. DBpedia helps here [<cite>Q27910422</cite>].

The following SPARQL query finds ten thousand (the default limit in <topic>DBpedia</topic>) Wikipedia pages with 
a `ChemBox` and checks for those if Wikidata has a SMILES:

<sparql>missingSMILES</sparql>

The results look like this:

<out limit="5">missingSMILES</out>

## Polymers without CXSMILES

Many <topic>polymers</topic> can have a <topic>CXSMILES</topic> property and the following query lists those that do not
have this property:

<sparql>polymersWithoutCXSMILES</sparql>

This returns values like this:

<out limit="5">polymersWithoutCXSMILES</out>

## Functional groups without CXSMILES

We can do the same thing for <topic>functional groups</topic>:

<sparql>functionalGroupsWithoutCXSMILES</sparql>

Here too, the list provides a list of curation opportunities:

<out limit="5">functionalGroupsWithoutCXSMILES</out>

## References

<references/>
