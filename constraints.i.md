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

## References

<references/>
