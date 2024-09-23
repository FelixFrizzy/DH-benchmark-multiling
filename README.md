[![DOI](https://zenodo.org/badge/824415368.svg)](https://zenodo.org/doi/10.5281/zenodo.12731599)

# Multilingual Archaeology Benchmark Dataset for Ontology Matching

## Description

This is a benchmark dataset for ontology matching created by Felix Kraus. It is based on an archaeology test case of the [DH benchmark dataset](https://github.com/FelixFrizzy/DH-benchmark), with focus on multilinguality. You can find all the general information about the dataset that you need for using it at the [OAEI](https://oaei.ontologymatching.org/) in this repository.
For further information on the [OAEI 2024](http://oaei.ontologymatching.org/2024/) see also [here](https://felixfrizzy.github.io/DH-benchmark-multiling/).   
This benchmark dataset facilitaes the development of ontology matching systems for datasets in different languages in the Digital Humanities on the example of archaeology. The systems face special obstacles which are at least partly addressed in this dataset:

- ontologies using only a single language that is not English
- domain-specific terms with a small research community at times
- use of a data model suitable for easily creating knowledge organization systems

## Test Cases

The dataset includes several test cases all based on the [archaeology test case "idai-pactols"](https://github.com/FelixFrizzy/DH-benchmark/tree/main/arch2_idai-pactols) from the [DH benchmark dataset](https://github.com/FelixFrizzy/DH-benchmark). Each test case consists of a monolingual source ontology, a monolingual target ontology and a manually compiled reference alignment. Only equivalent relations ("=") are targeted.

### Source Ontologies

There were two different vocabularies used for the ten different test cases:
- [PACTOLS](https://isl.ics.forth.gr/bbt-federated-thesaurus/PACTOLS/en/) [1]
    - Adapted version: Only narrower terms and direct ancestors of the concept "[archaeological site](https://ark.frantiq.fr/ark:/26678/pcrt9PJh9aTXv4)" were used
    - About 70 terms
    - Languages: Arabic, Dutch, English, French, German, Italian, Spanish
- [iDAI.world](https://isl.ics.forth.gr/bbt-federated-thesaurus/DAI/en/) [2]
    - Adapted version: Only narrower terms and direct ancestors of the concept "[material things](http://thesauri.da2inst.org/_1c0fa2d2)" were used
    - About 2600 terms
    - Major languages: Arabic, English, French, German, Italian

### Test case combinations
For all test cases, the source is DEFC and the target is PACTOLS. There exist the following combinations of monolingual ontologies:
- de-de
- de-en
- de-fr
- de-it
- en-en
- en-fr
- en-it
- fr-fr
- fr-it
- it-it



## Test Case Design
There are four common langauges of the two ontologies: English, French, German, Italian. To create the different test cases, all languages but one was removed from the ontology. This was done using a [script](https://github.com/FelixFrizzy/rdf-tools/tree/main/remove-language) developed for this purpose by the track authors. This leads to 10 different combinations of monolingual ontologies. 

The reference was also taken from the DH benchmark dataset. Terms in the reference that do not exist in the language of the monolingual ontology are removed accordingly from the reference. 

## Reference Alignment Methodology / Provenance
See the corresponding section of the [DH benchmark dataset](https://github.com/FelixFrizzy/DH-benchmark?tab=readme-ov-file#reference-alignment-methodology--provenance). 

# References / License Information
## Controlled Vocabularies
[1]: [PACTOLS](https://isl.ics.forth.gr/bbt-federated-thesaurus/PACTOLS/en/) (adapted) [[ODbL v1.0](https://opendatacommons.org/licenses/odbl/1-0/); Creators: Groupe PACTOLS/FRANTIQ]  
[2]: [iDAI.world](https://isl.ics.forth.gr/bbt-federated-thesaurus/DAI/en/) (adapted)[](https://vocabs.dariah.eu/defc_thesaurus/en/) [[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.en); Creators: Annika Kirscheneder, Camilla Colombi, Elenore Pape, Gabriele Rasbach, Henriette Senst, Lena Vitt, Matthias Block, Nina Dworschak, Reinhard Förtsch, Sabine Thänert]  

# Contact information
- Creator: Felix Kraus
- Email (subsitute accordingly): firstname.lastname (at) kit (dot) edu
- License owner: Karlsruhe Institute of Technology (KIT)
