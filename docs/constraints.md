# Wikidata property constraints

One way to keep control over the content of Wikidata is provided by Wikidata itself. These
are the <a name="tp1">property constraints</a>. For example, the property for the <a name="tp2">isomeric SMILES</a> requires
that each item in Wikidata has a different value (`distinct-values constraint`) and
can have only one (best) value (`single-best-value constraint`). Many properties also
use a regular expression to describe allowed values (`format constraint`).

Using these constraints, automated tests are routinely run resulting in reports. Not
all contraint violation, however, is a true error, and the mechanism does allow for
exceptions to be recorded. <!-- add example? --> For example, for the
<a name="tp3">MassBank accession ID</a>, format violations are reported, unique value violations, and more.

These reports provide both curators and users to get an idea of the status of the
chemistry in Wikidata.

For up-to-date information about properties used for chemicals: <https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry/Properties#Up-to-date_list_of_properties_about_chemical>

## References


