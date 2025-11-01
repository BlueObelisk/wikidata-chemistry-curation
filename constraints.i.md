# Wikidata property constraints

One way to keep control over the content of Wikidata is provided by Wikidata itself. These
are the <topic>property constraints</topic>. For example, the property for the <topic>isomeric SMILES</topic> requires
that each item in Wikidata has a different value (`distinct-values constraint`) and
can have only one (best) value (`single-best-value constraint`). Many properties also
use a regular expression to describe allowed values (`format constraint`).

Using these constraints, automated tests are routinely run resulting in reports. Not
all contraint violation, however, is a true error, and the mechanism does allow for
exceptions to be recorded. <!-- add example? --> For example, for the
<topic>MassBank accession ID</topic>, format violations are reported, unique value violations, and more.

These reports provide both curators and users to get an idea of the status of the
chemistry in Wikidata.

For up-to-date information about properties used for chemicals: <https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry/Properties#Up-to-date_list_of_properties_about_chemical>

## Single value

Many external identifiers are expected to only be found on a single Wikidata items. This is particularly
the case when the external database uses the InChIKey has uniqueness criterion, like Wikidata.

All Wikidata properties have discussion pages that list constraint violations, and most of these
have matching SPARQL queries. For example, the <topic>ChEMBL ID</topic> has this following SPARQL
query to find ChEMBL identifiers used on more than one Wikidata item:

<sparql>P592UniqueValue</sparql>

While this query shows a few false positives caused by tautomerism, it provides a useful
list to regularly check:

<out limit="10">P592UniqueValue</out>

## Uniqe value

Smilarly, we can use SPARQL to find Wikidata items with more than one ChEMBL identifier:

<sparql>P592SingleValue</sparql>

This gives this list of Wikidata items with more than one ChEMBL ID:

<out limit="10">P592SingleValue</out>

## References

<references/>
