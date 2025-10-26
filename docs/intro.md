# Introduction

[Wikidata](https://wikidata.org/) is a useful resource in the linked data network [<a href="#citeref1">1</a>].
It has knowledge about more than 1.3 million chemical compounds, exceeding the number of compounds in Wikipedia.
Because every Wikipedia article has a matching Wikidata record, Wikipedia should be a subset. Several efforts
have taken place to add chemistry to Wikidata and some of that has been published.
For example, Waagmeester, Stupp, Burgstaller-Muehlbacher, and others wrote a bot to add relevant life science
knowledge to Wikidata, including small compounds [<a href="#citeref2">2</a>]. Rutz and others use Wikidata for
natural products [<a href="#citeref3">3</a>], and Willighagen and others recently wrote up an extension of
Scholia for Chemistry [<a href="#citeref4">4</a>].

The last raises the question how the quality control of the chemistry in Wikidata is handled. This ebook
aims to explain the methods we have at hand to do just that. It consists of several chapters explaining
the intrinsic property contraints, useful SPARQL queries, and cheminformatics-based scripts that detect
inconsistencies.

## References

1. <a name="citeref1"></a> Vrandečić D. Wikidata: A New Platform for Collaborative Data Collection. Proceedings of the 21st International Conference on World Wide Web. 2012;1063–4.  doi:[10.1145/2187980.2188242](https://doi.org/10.1145/2187980.2188242) ([Scholia](https://scholia.toolforge.org/doi/10.1145/2187980.2188242))
2. <a name="citeref2"></a> Waagmeester A, Stupp G, Burgstaller-Muehlbacher S, Good BM, Griffith M, Griffith O, et al. Wikidata as a knowledge graph for the life sciences. eLife [Internet]. 2020 Mar 17;9. Available from: https://elifesciences.org/articles/52614 doi:[10.7554/ELIFE.52614](https://doi.org/10.7554/ELIFE.52614) ([Scholia](https://scholia.toolforge.org/doi/10.7554/ELIFE.52614))
3. <a name="citeref3"></a> Rutz A, Sorokina M, Galgonek J, Mietchen D, Willighagen E, Gaudry A, et al. The LOTUS initiative for open knowledge management in natural products research. eLife [Internet]. 2022 May 26;11. Available from: https://doi.org/10.7554/elife.70780 doi:[10.7554/ELIFE.70780](https://doi.org/10.7554/ELIFE.70780) ([Scholia](https://scholia.toolforge.org/doi/10.7554/ELIFE.70780))
4. <a name="citeref4"></a> Willighagen E, Slenter D, Rutz A, Mietchen D, Nielsen FÅ. Scholia Chemistry: access to chemistry in Wikidata. ChemRxiv [Internet]. 2025 May 14; Available from: https://chemrxiv.org/engage/api-gateway/chemrxiv/assets/orp/resource/item/6820928550018ac7c57abf6b/original/scholia-chemistry-access-to-chemistry-in-wikidata.pdf doi:[10.26434/CHEMRXIV-2025-53N0W](https://doi.org/10.26434/CHEMRXIV-2025-53N0W) ([Scholia](https://scholia.toolforge.org/doi/10.26434/CHEMRXIV-2025-53N0W))

