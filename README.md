# Antimicrobial activity prediction against Escherichia coli from public ChEMBL and PubChem data

Predicts growth inhibition of Escherichia coli, the workhorse organism of antibacterial screening and consequently one of the better-covered pathogens in public data. Twelve binary classifiers were trained over separate ChEMBL and PubChem assay pools, keeping single-point percentage inhibition apart from dose-response MIC measurements since the two encode activity differently. A quality-weighted consensus combines them, favouring models built on larger and more reliable pools.

This model was incorporated on 2026-05-19.Last packaged on 2026-07-22.

## Information
### Identifiers
- **Ersilia Identifier:** `eos5eya`
- **Slug:** `antimicrobial-activity-ecoli`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Diarrheal diseases`, `Antimicrobial resistance`
- **Target Organism:** `Escherichia coli`
- **Tags:** `Gram-negative bacteria`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `13`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of Escherichia coli growth inhibition across twelve sub-models, plus a weighted consensus.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 12 sub-models. Recommended threshold: 0.855. |
| chembl_single_point_0 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 203 assays (2181 compounds). Recommended threshold: 0.714. |
| chembl_single_point_1 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 171 assays (1935 compounds). Recommended threshold: 0.716. |
| chembl_single_point_2 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 131 assays (1618 compounds). Recommended threshold: 0.767. |
| chembl_single_point_3 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 92 assays (1432 compounds). Recommended threshold: 0.738. |
| chembl_single_point_4 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 64 assays (872 compounds). Recommended threshold: 0.538. |
| chembl_single_point_5 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 68 assays (814 compounds; incl. 66 added negatives). Recommended threshold: 0.545. |
| chembl_dose_response_0 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 1675 assays (23876 compounds). Recommended threshold: 0.751. |
| chembl_dose_response_1 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 962 assays (11542 compounds). Recommended threshold: 0.729. |
| chembl_dose_response_2 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 591 assays (7935 compounds). Recommended threshold: 0.707. |

_10 of 13 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos5eya](https://hub.docker.com/r/ersiliaos/eos5eya)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos5eya.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos5eya.zip)

### Resource Consumption
- **Model Size (Mb):** `513`
- **Environment Size (Mb):** `7208`
- **Image Size (Mb):** `7784.05`

**Computational Performance (seconds):**
- 10 inputs: `59.13`
- 100 inputs: `53.82`
- 10000 inputs: `1534.9`

### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos5eya
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos5eya
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
