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

Part of these models can be expressed as <topic>shape expressions</topic>. For this, Wikidata uses ShEx (see [shex.io](https://shex.io/)).
These shape expressions formalize a data model and allow a computer to report inconsistency complementary
and extending the propery constraints. The use of of shape expressions has previously been used for
viruses, proteins, and genes [<cite>Q105037759</cite>].

### Chemical elements

<!-- TODO SPARQL instead of link -->
Some of them are linked to their corresponding item, some are not, see: <https://w.wiki/FqRc>

The following entity schema describe the basic models of:

* [EntitySchema:E46](https://www.wikidata.org/wiki/EntitySchema:E46): <topic>chemical element</topic>
* [EntitySchema:E47](https://www.wikidata.org/wiki/EntitySchema:E47): <topic>racemic mixture</topic>
* [EntitySchema:E406](https://www.wikidata.org/wiki/EntitySchema:E406): <topic>type of a chemical entity</topic>
* [EntitySchema:E232](https://www.wikidata.org/wiki/EntitySchema:E232): <topic>lipid</topic>
* [EntitySchema:E240](https://www.wikidata.org/wiki/EntitySchema:E240): <topic>natural product</topic>

## References

<references/>
