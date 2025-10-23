# Results of the [Archaeology multilingual track](https://oaei.ontologymatching.org/2025/digitalhumanities/index.html) of the [OAEI 2025 campaign](https://oaei.ontologymatching.org/2025/)
OAEI 2025 is the first year for the archaeology track to participate. For information about the goal of this track and information about the test cases, refer to the [Readme](https://github.com/FelixFrizzy/DH-benchmark-multiling/blob/main/README.md).

# Evaluation Modalities
We used dataset v1.0.0 (https://doi.org/10.5281/zenodo.12731599) and precision, recall and F1-score for evaluation and only evaluated equivalence relationships. If matching systems resulted in either errors or zero identified matches, we considered them as failed. Adhering the [OAEI rules](https://oaei.ontologymatching.org/doc/oaei-rules.2.html), we didn't change any settings for the matching systems. 

## Resources
- VM with 8 x 2.4 GHz cores, 16GB RAM

## Steps to Reproduce the Results
- Download the evaluation client [evaluation client](https://nightly.link/dwslab/melt/workflows/java_client_upload/master/evaluation-client.zip) as explained in the [documentation](https://dwslab.github.io/melt/matcher-evaluation/client).
- Download the 2025 (or any other MELT compatible) matchers and put them in the same folder.
- Run the command
```bash
java -jar matching-eval-client-latest.jar --systems logmap-melt-oaei-2021-web-latest.tar.gz logmap-bio-melt-oaei-2021-web-latest.tar.gz logmap-kg-melt-oaei-2021-web-latest.tar.gz logmap-lite-melt-oaei-2021-web-latest.tar.gz matcha.tar.gz "ALIN - Jomar Silva.zip" MDMapper-seals.zip https://match.tomato.irit.fr/match --track http://oaei.webdatacommons.org/tdrs/ archaeology 2024all --results oaei2025_arch
```

# Evaluation Results
The raw results can be found in the `raw-results_archtrack_2025` folder in this repo.

## Overview over the matching systems
- Running successfully
    - Agent-OM (see note below)
    - LogMap Bio
    - LogMap KG
    - Logmap
    - Matcha
    - TIM
- Running without code errors / exceptions, alignments empty
    - LSMatch
    - LSMatch-Multilingual
- Running with exceptions / error, no alignments received
    - ALIN
    - MDMapper

Note on Agent-OM: The results of Agent-OM were provided by the system authors and could not be verified by executing the system using MELT.

## Recall, Precision, F1-Score

| Test Case               |Precision |           |            |           |            |Recall    |            |           |            |F1-Score    |            |           |          |          |            |           |            |       |
| ----------------------- | -------- | --------- | ---------- | --------- | ---------- | -------- | ---------- | --------- | ---------- | ---------- | ---------- | --------- | -------- | -------- | ---------- | --------- | ---------- | ----- |
|                         | Agent-OM | LogMap    | LogMap Bio | LogMap KG | Matcha     | TIM      | Agent OM   | LogMap    | LogMap Bio | LogMap KG  | Matcha     | TIM       | AgentOM  | LogMap   | LogMap Bio | LogMap KG | Matcha     | TIM   |
| idai-pactols_de-de      | 0.75     | 0.85      | 0.91       | 0.91      | **1.00**   | 0.00     | 0.35       | **0.65**  | 0.59       | 0.59       | 0.12       | 0.00      | 0.48     | **0.73** | 0.71       | 0.71      | 0.21       | 0.00  |
| idai-pactols_de-en      | **0.50** | 0.25      | 0.33       | 0.33      | 0.17       | 0.00     | **0.29**   | 0.06      | 0.06       | 0.06       | 0.06       | 0.00      | **0.37** | 0.10     | 0.10       | 0.10      | 0.09       | 0.00  |
| idai-pactols_de-fr      | **0.67** | 0.40      | 0.40       | 0.40      | 0.33       | 0.00     | **0.12**   | **0.12**  | **0.12**   | **0.12**   | **0.12**   | 0.00      | **0.20** | 0.18     | 0.18       | 0.18      | 0.17       | 0.00  |
| idai-pactols_de-it      | 0.33     | **0.50**  | **0.50**   | **0.50**  | 0.40       | 0.00     | 0.06       | **0.12**  | **0.12**   | **0.12**   | **0.12**   | 0.00      | 0.10     | **0.19** | **0.19**   | **0.19**  | 0.18       | 0.00  |
| idai-pactols_en-en      | 0.60     | 0.27      | 0.60       | 0.60      | **0.75**   | 0.00     | 0.50       | **0.67**  | 0.50       | 0.50       | 0.50       | 0.00      | 0.55     | 0.38     | 0.55       | 0.55      | **0.60**   | 0.00  |
| idai-pactols_en-fr      | 0.67     | 0.13      | **1.00**   | **1.00**  | 0.33       | 0.00     | **0.33**   | 0.17      | 0.17       | 0.17       | 0.17       | 0.00      | **0.44** | 0.14     | 0.29       | 0.29      | 0.22       | 0.00  |
| idai-pactols_en-it      | 0.33     | 0.50      | **1.00**   | **1.00**  | 0.50       | 0.00     | **0.33**   | 0.17      | 0.17       | 0.17       | 0.17       | 0.00      | **0.33** | 0.25     | 0.29       | 0.29      | 0.25       | 0.00  |
| idai-pactols_fr-fr      | **0.25** | 0.09      | 0.13       | 0.13      | **0.25**   | 0.02     | **0.25**   | **0.25**  | **0.25**   | **0.25**   | **0.25**   | **0.25**  | **0.25** | 0.13     | 0.17       | 0.17      | **0.25**   | 0.03  |
| idai-pactols_fr-it      | **0.20** | 0.00      | 0.00       | 0.00      | 0.00       | 0.00     | **0.25**   | 0.00      | 0.00       | 0.00       | 0.00       | 0.00      | **0.22** | 0.00     | 0.00       | 0.00      | 0.00       | 0.00  |
| idai-pactols_it-it      | 0.22     | 0.17      | 0.10       | 0.10      | **0.30**   | 0.02     | 0.50       | **0.75**  | 0.25       | 0.25       | **0.75**   | 0.25      | 0.31     | 0.27     | 0.14       | 0.14      | **0.43**   | 0.04  |
| Average over all tracks | 0.45     | 0.31      | **0.50**   | **0.50**  | 0.40       | 0.00     | **0.30**   | 0.29      | 0.22       | 0.22       | 0.23       | 0.05      | **0.33** | 0.24     | 0.26       | 0.26      | 0.24       | 0.01  |




## Average (mean) over matchers

| Test Case               | Precision (average) | Recall (average) | F1-score (average) |
|-------------------------|---------------------|------------------|--------------------|
| idai-pactols_de-de      | 0.74                |             0.38 |               0.47 |
| idai-pactols_de-en      | 0.26                |             0.09 |               0.13 |
| idai-pactols_de-fr      | 0.37                |             0.10 |               0.15 |
| idai-pactols_de-it      | 0.37                |             0.09 |               0.14 |
| idai-pactols_en-en      | 0.47                |             0.45 |               0.44 |
| idai-pactols_en-fr      | 0.52                |             0.17 |               0.23 |
| idai-pactols_en-it      | 0.56                |             0.17 |               0.24 |
| idai-pactols_fr-fr      | 0.15                |             0.25 |               0.17 |
| idai-pactols_fr-it      | 0.03                |             0.04 |               0.04 |
| idai-pactols_it-it      | 0.15                |             0.46 |               0.22 |
| Average over all tracks | 0.33                |             0.20 |               0.21 |



## Runtimes
| Matcher              | total runtime (hh:mm:ss) |
|----------------------|--------------------------|
| Agent-OM             | not provided             |
| LogMap               | 00:00:14                 |
| LogMap Bio           | 00:00:18                 |
| LogMap KG            | 00:00:13                 |
| LogMap lite          | 01:02:30                 |
| LSMatch              | 00:00:22                 |
| LSMatch Multilingual | 00:00:23                 |
| Matcha               | 00:10:42                 |
| TIM                  | 00:00:10                 |

## Discussion
When looking at the F1-scores averaged over all matchers, they range from 0.04 to 0.47. Only the language combinations en-en and de-de are on the upper end, while all the others are at or below 0.24. Compared to last year, one system, Agent-OM, now finds alignments for the language combination fr-it which is a significant improvement. 

Comparing the matching systems, Agent-OM performs best with an averaged F1-score of 0.33, closely followed by the LogMap family and Matcha. TIM failed to produce any alignments for almost all test cases.

The execution times are below half a minute for the whole track, except Matcha and LogMap lite, with the latter returning only empty alignments. 

It can clearly be seen that handling languages other than English needs to be addressed by matching systems. This is particularly important for making matching systems useful for domains like the Digital Humanities where research objects are in multiple languages and the research itself is frequently conducted in the local language of the respective research institution.

# Acknowledgement
The execution of this evaluation was funded by the research program “Engineering Digital Futures” of the Helmholtz Association of German Research Centers.
