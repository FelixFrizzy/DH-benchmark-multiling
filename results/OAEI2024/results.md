# Results of the [Archaeology multilingual track](https://oaei.ontologymatching.org/2024/digitalhumanities/index.html) of the [OAEI 2024 campaign](https://oaei.ontologymatching.org/2024/)
OAEI 2024 is the first year for the archaeology track to participate. For information about the goal of this track and information about the test cases, refer to the [Readme](https://github.com/FelixFrizzy/DH-benchmark-multiling/blob/main/README.md).

# Evaluation Modalities
We used dataset v1.0.0 (https://doi.org/10.5281/zenodo.12731599) and precision, recall and F1-score for evaluation and only evaluated equivalence relationships. If matching systems resulted in either errors or zero identified matches, we considered them as failed. Adhering the [OAEI rules](https://oaei.ontologymatching.org/doc/oaei-rules.2.html), we didn't change any settings for the matching systems. 

## Resources
- VM with 8 x 2.4 GHz cores, 16GB RAM

## Steps to Reproduce the Results
- Download the evaluation client [evaluation client](https://nightly.link/dwslab/melt/workflows/java_client_upload/master/evaluation-client.zip) as explained in the [documentation](https://dwslab.github.io/melt/matcher-evaluation/client).
- Download the 2024 (or any other MELT compatible) matchers and put them in the same folder.
- Run the command
```bash
java -jar matching-eval-client-latest.jar --systems logmap-melt-oaei-2021-web-latest.tar.gz logmap-bio-melt-oaei-2021-web-latest.tar.gz logmap-kg-melt-oaei-2021-web-latest.tar.gz logmap-lite-melt-oaei-2021-web-latest.tar.gz matcha.tar.gz "ALIN - Jomar Silva.zip" MDMapper-seals.zip https://match.tomato.irit.fr/match --track http://oaei.webdatacommons.org/tdrs/ archaeology 2024all --results oaei2024_arch
```

# Evaluation Results
The raw results can be found in the `raw-results_archtrack_2024` folder in this repo.

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

| Test Case               |Precision |            |           |          |Recall    |            |           |          |F1-Score  |            |           |          |
| ----------------------- | -------- | ---------- | --------- | -------- | -------- | ---------- | --------- | -------- | -------- | ---------- | --------- | -------- |
|                         | LogMap   | LogMap Bio | LogMap KG | Matcha   | LogMap   | LogMap Bio | LogMap KG | Matcha   | LogMap   | LogMap Bio | LogMap KG | Matcha   |
| idai-pactols_de-de      | 0.85     | 0.91       | 0.91      | **1.00** | **0.65** | 0.59       | 0.59      | 0.12     | **0.73** | 0.71       | 0.71      | 0.21     |
| idai-pactols_de-en      | 0.25     | **0.33**   | **0.33**  | 0.02     | **0.06** | **0.06**   | **0.06**  | **0.06** | **0.10** | **0.10**   | **0.10**  | 0.03     |
| idai-pactols_de-fr      | **0.40** | **0.40**   | **0.40**  | 0.04     | 0.12     | 0.12       | 0.12      | **0.18** | **0.18** | **0.18**   | **0.18**  | 0.07     |
| idai-pactols_de-it      | **0.50** | **0.50**   | **0.50**  | 0.00     | **0.12** | **0.12**   | **0.12**  | 0.00     | **0.19** | **0.19**   | **0.19**  | 0.00     |
| idai-pactols_en-en      | 0.27     | 0.60       | 0.60      | **0.75** | **0.67** | 0.50       | 0.50      | 0.50     | 0.38     | 0.55       | 0.55      | **0.60** |
| idai-pactols_en-fr      | 0.13     | **1.00**   | **1.00**  | 0.03     | 0.17     | 0.17       | 0.17      | **0.33** | 0.14     | **0.29**   | **0.29**  | 0.05     |
| idai-pactols_en-it      | 0.50     | **1.00**   | **1.00**  | 0.00     | **0.17** | **0.17**   |  **0.17** | 0.00     | 0.25     | **0.29**   | **0.29**  | 0.00     |
| idai-pactols_fr-fr      | 0.09     | 0.13       | 0.13      | **0.25** | **0.25** | **0.25**   | **0.25**  | **0.25** | 0.13     | 0.17       | 0.17      | **0.25** |
| idai-pactols_fr-it      | \-       | \-         | \-        | \-       | \-       | \-         | \-        | \-       | \-       | \-         | \-        | \-       |
| idai-pactols_it-it      | 0.17     | 0.10       | 0.10      | **0.30** | **0.75** | 0.25       | 0.25      | **0.75** | 0.27     | 0.14       | 0.14      | **0.43** |
| Average over all tracks | 0.35     | **0.55**   | **0.55**  | 0.27     | **0.33** | 0.25       | 0.25      | 0.24     | 0.26     | **0.29**   | **0.29**  | 0.18     |


## Average (mean) over matchers

| Test Case               | Precision (average) | Recall (average) | F1-score (average) |
|-------------------------|---------------------|------------------|--------------------|
| idai-pactols_de-de      | 0.92                | 0.49             | 0.59               |
| idai-pactols_de-en      | 0.23                | 0.06             | 0.08               |
| idai-pactols_de-fr      | 0.31                | 0.13             | 0.15               |
| idai-pactols_de-it      | 0.38                | 0.09             | 0.14               |
| idai-pactols_en-en      | 0.55                | 0.54             | 0.52               |
| idai-pactols_en-fr      | 0.54                | 0.21             | 0.19               |
| idai-pactols_en-it      | 0.63                | 0.13             | 0.21               |
| idai-pactols_fr-fr      | 0.15                | 0.25             | 0.18               |
| idai-pactols_fr-it      |                     |                  | -                  |
| idai-pactols_it-it      | 0.17                | 0.50             | 0.25               |
| Average over all tracks | 0.43                | 0.27             | 0.26               |


## Runtimes
| Matchers    | total runtime (hh:mm:ss) |
|-------------|--------------------------|
| LogMap      | 00:00:13                 |
| LogMap Bio  | 00:00:19                 |
| LogMap KG   | 00:00:12                 |
| LogMap lite | 00:55:03                 |
| Matcha      | 02:31:50                 |
| TOMATO      | 00:00:27                 |

## Discussion
When looking at the F1-scores averaged over all matchers, they range from 0.08 to 0.56. Only the language combinations en-en and de-de are on the upper end, while all the others are at or below 0.24. This suggests that most systems struggle when dealing with different languages. The fact that German and English both belong to the West Germanic languages might be advantageous. The romance languages pose a bigger challenge that the systems cannot solve in large parts. 

Comparing the matching systems, LogMap Bio and LogMap KG perform best with an averaged F1-score of 0.29. 

The execution times are below half a minute for the whole track, except LogMap lite (55min) and Matcha (2h31min). The latter two only resulted in empty alignments. 

It can clearly seen that handling languages other than English needs to be addressed by matching systems. This is particularly important for making matching systems useful for domains like the Digital Humanities where research objects are in multiple languages and the research itself is frequently conducted in the local langauge of the respective research institution.

# Acknowledgement
The execution of this evaluation was funded by the research program “Engineering Digital Futures” of the Helmholtz Association of German Research Centers.
