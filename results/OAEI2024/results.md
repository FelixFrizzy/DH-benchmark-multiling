This folder contains the results of the multilingual [archaeology track](https://oaei.ontologymatching.org/2024/archaeology/index.html) of the [OAEI 2024 campaign](https://oaei.ontologymatching.org/2024/). 

## Resources
- VM with 8 x 2.4 GHz cores, 16GB RAM

## Steps to reproduce results
- Download the evaluation client [evaluation client](https://nightly.link/dwslab/melt/workflows/java_client_upload/master/evaluation-client.zip) as explained in the [documentation](https://dwslab.github.io/melt/matcher-evaluation/client).
- Download the 2024 (or any other MELT compatible) matchers and put them in the same folder.
- Run the command
```bash
java -jar matching-eval-client-latest.jar --systems logmap-melt-oaei-2021-web-latest.tar.gz logmap-bio-melt-oaei-2021-web-latest.tar.gz logmap-kg-melt-oaei-2021-web-latest.tar.gz logmap-lite-melt-oaei-2021-web-latest.tar.gz matcha.tar.gz "ALIN - Jomar Silva.zip" MDMapper-seals.zip https://match.tomato.irit.fr/match --track http://oaei.webdatacommons.org/tdrs/ archaeology 2024all --results oaei2024_arch
```
The raw results can be found in the `raw-results_archtrack_2024` folder in this repo.

# Results


## Overview over the matching systems
- Running successfully
    - Matcha
    - LogMap Bio
    - LogMap KG
    - Logmap
- Running without code errors / exceptions, alignments empty
    - TOMATO
    - LogMap lite
- Running with exceptions / error, no alignments received
    - ALIN
    - MDMapper
    - OntoMatch (standalone, not possible to run with MELT / SEALS)

## Recall, Precision, F1-Score
(table)


## Runtimes
(table)

## Discussion
When looking at the F1-scores averaged over all matchers, they range from 0.08 to 0.56. Only the language combinations en-en and de-de are on the upper end, while all the others are at or below 0.24. This suggests that most systems struggle when dealing with different languages. The fact that German and English both belong to the West Germanic languages might be advantageous. The romance languages pose a bigger challenge that the systems cannot solve in large parts. 

Comparing the matching systems, LogMap Bio and LogMap KG perform best with an averaged F1-score of 0.29. 

The execution times are below half a minute for the whole track, except LogMap lite (55min) and Matcha (2h31min). The latter two only resulted in empty alignments. 

It can clearly seen that handling languages other than English needs to be addressed by matching systems. This is particularly important for making matching systems useful for domains like the Digital Humanities where research objects are in multiple languages and the research itself is frequently conducted in the local langauge of the respective research institution.

# Acknowledgement
The execution of this evaluation was funded by the research program “Engineering Digital Futures” of the Helmholtz Association of German Research Centers.