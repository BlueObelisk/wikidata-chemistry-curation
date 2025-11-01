# Models of chemistry

The [Wikidata:WikiProject Chemistry](https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry) is the primary
source describing the data models used for chemistry in Wikidata. It is also the place where discussions are held
about these topics. Over time, the model has evolved. We do not intend to repeat all the content, but we will
highlight some aspects reflecting how Wikidata thinks about chemistry and the quality of the chemistry data
in Wikidata.

## Model and guidance

Most of the modelling of chemical entries in Wikidata is described in the aforementioned *WikiProject_Chemistry*.
The project provides many guidelines of the structure of methods.

### Wikidata guidelines

An overview of guidelines is given in <https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry/Guidelines>

A principle guideline is that any chemical is modelled *instance of* (P31) *type of chemical entity* (Q113145171)
for specific chemical, but as one of the many available metaclasses.

#### Basic metaclasses and relations

This page describes the main classes of chemical entities, such as *structural class of chemical entities* (Q47154513),
*group of stereoisomers* (Q59199015), and *class of chemical entities with similar applications or functions* (Q56256173).
A full overview is found at <https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry/Guidelines/Basic_metaclasses_and_relations>

#### Entities with undefined isomeric or isotopic features

Specific guidelines exist, such as for undefined isomeric or isotopic features:
<https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry/Guidelines/Entities_with_undefined_isomeric_or_isotopic_features>

#### Naming conventions

<https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry/Guidelines/Naming_conventions>

#### Illustrations

<https://www.wikidata.org/wiki/Wikidata:WikiProject_Chemistry/Guidelines/Illustrations>

## Shape expressions

Part of these models can be expressed as <a name="tp1">shape expressions</a>. For this, Wikidata uses ShEx (see [shex.io](https://shex.io/)).
These shape expressions formalize a data model and allow a computer to report inconsistency complementary
and extending the propery constraints. The use of of shape expressions has previously been used for
viruses, proteins, and genes [<a href="#citeref1">1</a>].

### Chemical elements

<!-- TODO SPARQL instead of link -->
Some of them are linked to their corresponding item, some are not, see: <https://w.wiki/FqRc>

The following entity schema describe the basic models of:

* [EntitySchema:E46](https://www.wikidata.org/wiki/EntitySchema:E46): <a name="tp2">chemical element</a>
* [EntitySchema:E47](https://www.wikidata.org/wiki/EntitySchema:E47): <a name="tp3">racemic mixture</a>
* [EntitySchema:E406](https://www.wikidata.org/wiki/EntitySchema:E406): <a name="tp4">type of a chemical entity</a>
* [EntitySchema:E232](https://www.wikidata.org/wiki/EntitySchema:E232): <a name="tp5">lipid</a>
* [EntitySchema:E240](https://www.wikidata.org/wiki/EntitySchema:E240): <a name="tp6">natural product</a>

## References

1. <a name="citeref1"></a> Waagmeester A, Willighagen EL, Su AI, Kutmon M, Gayo JEL, Fernández-Álvarez D, et al. A protocol for adding knowledge to Wikidata: aligning resources on human coronaviruses. BMC Biol [Internet]. 2021 Jan 22;19(1):12. Available from: https://bmcbiol.biomedcentral.com/track/pdf/10.1186/s12915-020-00940-y.pdf doi:[10.1186/S12915-020-00940-Y](https://doi.org/10.1186/S12915-020-00940-Y) ([Scholia](https://scholia.toolforge.org/doi/10.1186/S12915-020-00940-Y))

