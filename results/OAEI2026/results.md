# Results of the [Archaeology multilingual track](https://oaei.ontologymatching.org/2026/digitalhumanities/index.html) of the [OAEI 2026 campaign](https://oaei.ontologymatching.org/2026/)
OAEI 2026 is the first year for the archaeology track to participate. For information about the goal of this track and information about the test cases, refer to the [Readme](https://github.com/FelixFrizzy/DH-benchmark-multiling/blob/main/README.md).

# Evaluation Modalities
We used dataset v1.1.0 (https://doi.org/10.5281/zenodo.12731599) and precision, recall and F1-score for evaluation and only evaluated equivalence relationships. If matching systems resulted in either errors or zero identified matches, we considered them as failed. Adhering the [OAEI rules](https://oaei.ontologymatching.org/doc/oaei-rules.2.html), we didn't change any settings for the matching systems. 

## Resources
- VM with 8 x 2.4 GHz cores, 16GB RAM

## Steps to Reproduce the Results
- Download the evaluation client [evaluation client](https://nightly.link/dwslab/melt/workflows/java_client_upload/master/evaluation-client.zip) as explained in the [documentation](https://dwslab.github.io/melt/matcher-evaluation/client).
- Download the 2026 (or any other MELT compatible) matchers and put them in the same folder.
- Run the command
```bash
java -jar matching-eval-client-latest.jar \
  --systems \
  ../Matcher/2026/ALIN-2026.zip \
  ../Matcher/2026/logmap-2026.tar.gz \
  ../Matcher/2026/logmap-bio-2026.tar.gz \
  ../Matcher/2026/logmap-kg-2026.tar.gz \
  ../Matcher/2026/logmap-lite-2026.tar.gz \
  ../Matcher/2026/lsmatch-2026.tar.gz \
  ../Matcher/2026/lsmatch-multilingual-2026.tar.gz \
  ../Matcher/2026/matcha-2026.tar.gz \
  ../Matcher/2026/relmap-2026.tar.gz \
  ../Matcher/2026/secea-2026.tar.gz \
  ../Matcher/2026/tim-2026.tar.gz \
  --track http://oaei.webdatacommons.org/tdrs/ archaeology 2024all \
  --results oaei2026_archmultiling
```

# Evaluation Results
The raw results can be found in the `raw-results_archtrack_2026` folder in this repo.

## Overview over the matching systems
- Running successfully
    - LogMap KG
    - Matcha
    - SECEA (`de-de` successful; errors for the other nine test cases)
    - TIM
- Running without code errors / exceptions, no instance alignments
    - LogMap
    - LogMap Bio
    - LogMap lite
    - LSMatch
    - LSMatch Multilingual
- Running with exceptions / errors, no alignments received
    - ALIN
    - RelMap

Note on Agent-OM: The results of Agent-OM were provided by the system authors and could not be verified by executing the system using MELT.

## Recall, Precision, F1-Score
## Precision, Recall, F1-Score

| Test Case | Precision |  |  |  | Recall |  |  |  | F1-Score |  |  |  |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
|  | LogMap KG | Matcha | SECEA | TIM | LogMap KG | Matcha | SECEA | TIM | LogMap KG | Matcha | SECEA | TIM |
| idai-pactols_de-de | 0.83 | **1.00** | 0.08 | 0.50 | **0.59** | 0.12 | 0.12 | 0.12 | **0.69** | 0.21 | 0.10 | 0.19 |
| idai-pactols_de-en | **0.25** | 0.11 | 0.00* | 0.00 | 0.06 | **0.24** | 0.00* | 0.00 | 0.10 | **0.15** | 0.00* | 0.00 |
| idai-pactols_de-fr | **0.33** | 0.11 | 0.00* | 0.00 | 0.12 | **0.29** | 0.00* | 0.00 | **0.17** | 0.16 | 0.00* | 0.00 |
| idai-pactols_de-it | **0.40** | 0.10 | 0.00* | 0.00 | 0.12 | **0.24** | 0.00* | 0.00 | **0.18** | 0.14 | 0.00* | 0.00 |
| idai-pactols_en-en | 0.50 | **0.75** | 0.00* | 0.33 | **0.50** | **0.50** | 0.00* | 0.17 | 0.50 | **0.60** | 0.00* | 0.22 |
| idai-pactols_en-fr | **0.50** | 0.09 | 0.00* | 0.00 | 0.17 | **0.67** | 0.00* | 0.00 | **0.25** | 0.16 | 0.00* | 0.00 |
| idai-pactols_en-it | **0.50** | 0.08 | 0.00* | 0.00 | 0.17 | **0.50** | 0.00* | 0.00 | **0.25** | 0.13 | 0.00* | 0.00 |
| idai-pactols_fr-fr | 0.11 | **0.25** | 0.00* | 0.20 | **0.25** | **0.25** | 0.00* | **0.25** | 0.15 | **0.25** | 0.00* | 0.22 |
| idai-pactols_fr-it | 0.00 | **0.05** | 0.00* | 0.00 | 0.00 | **0.50** | 0.00* | 0.00 | 0.00 | **0.09** | 0.00* | 0.00 |
| idai-pactols_it-it | 0.09 | **0.30** | 0.00* | 0.25 | 0.25 | **0.75** | 0.00* | 0.25 | 0.13 | **0.43** | 0.00* | 0.25 |
| Average over all tracks | **0.35** | 0.28 | 0.01 | 0.13 | 0.22 | **0.40** | 0.01 | 0.08 | **0.24** | 0.23 | 0.01 | 0.09 |

\* This test case was not successful and is treated as zero when calculating averages. This applies to SECEA on all language combinations except `de-de`.

All scores are displayed to two decimal places. Bold marks the highest displayed value in each metric group, including ties.

## Average (mean) over matchers

| Test Case | Precision | Recall | F1-Score |
| --- | ---: | ---: | ---: |
| idai-pactols_de-de | 0.60 | 0.24 | 0.30 |
| idai-pactols_de-en | 0.09 | 0.07 | 0.06 |
| idai-pactols_de-fr | 0.11 | 0.10 | 0.08 |
| idai-pactols_de-it | 0.13 | 0.09 | 0.08 |
| idai-pactols_en-en | 0.40 | 0.29 | 0.33 |
| idai-pactols_en-fr | 0.15 | 0.21 | 0.10 |
| idai-pactols_en-it | 0.14 | 0.17 | 0.10 |
| idai-pactols_fr-fr | 0.14 | 0.19 | 0.16 |
| idai-pactols_fr-it | 0.01 | 0.13 | 0.02 |
| idai-pactols_it-it | 0.16 | 0.31 | 0.20 |
| Average over all tracks | 0.19 | 0.18 | 0.14 |

## Runtimes

| Matcher | Total runtime (hh:mm:ss) |
| --- | ---: |
| LogMap KG | 00:00:19 |
| Matcha | 00:10:11 |
| SECEA | 00:00:01 |
| TIM | 00:00:10 |

The runtime for SECEA covers only the successful `de-de` test case. It does not represent a successful run over the full track.

## Discussion

When looking at the F1-scores averaged over all matchers, they range from 0.02 to 0.33. The language combinations en-en and de-de perform best, while all others remain at or below 0.20. Matcha now finds correct alignments for fr-it, where only Agent-OM was successful last year.

Comparing the matching systems, LogMap KG has the best average F1-score of 0.24, followed by Matcha with 0.23. Both remain close to last year's results. TIM improved from 0.01 to 0.09, but still only finds correct alignments when both vocabularies use the same language. The newcomer SECEA was successful only on de-de and resulted in errors for the other nine test cases, giving an average F1-score of 0.01 when these failures are treated as zero.

On the downside, LogMap and LogMap Bio, which were successful last year, did not find any instance alignments this year. LogMap KG was the only successful LogMap variant.

LogMap KG and TIM need 19 and 10 seconds for the whole track, while Matcha needs 10 minutes and 11 seconds. 

Handling different languages remains a problem for matching systems. This is particularly important for domains like the Digital Humanities, where research objects are in multiple languages and research is frequently conducted in the local language of the respective research institution.

# Acknowledgement
The execution of this evaluation was funded by the research program “Engineering Digital Futures” of the Helmholtz Association of German Research Centers.
