# Antimicrobial activity prediction against Escherichia coli from public ChEMBL and PubChem data

Bioactivity prediction of growth inhibition in Escherichia coli, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL and PubChem. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (percent inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.


## Information
### Identifiers
- **Ersilia Identifier:** `eos5eya`
- **Slug:** `antimicrobial-activity-ecoli`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Diarrheal diseases`
- **Target Organism:** `Escherichia coli`
- **Tags:** `Gram-negative bacteria`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `28`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Escherichia coli from 27 ChEMBL- and PubChem-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 27 sub-models. Recommended threshold: 0.953. |
| individual_mic_decoys | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL679318 (MIC; cutoff 10 uM; n=1110 incl. decoys). Recommended threshold: 0.900. |
| individual_gi_decoys | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4011045 (growth inhibition %; cutoff 50%; n=1030 incl. decoys). Recommended threshold: 0.895. |
| merged_mic_decoys_c | float | high | Probability from sub-model trained on MIC measurements merged across 6 ChEMBL assays (cutoff 10 uM; n=1690 incl. decoys). Recommended threshold: 0.867. |
| merged_mic_decoys_e | float | high | Probability from sub-model trained on MIC measurements merged across 10 ChEMBL assays (cutoff 20 uM; n=1500 incl. decoys). Recommended threshold: 0.872. |
| merged_mic_decoys_b | float | high | Probability from sub-model trained on MIC measurements merged across 21 ChEMBL assays (cutoff 20 uM; n=1180 incl. decoys). Recommended threshold: 0.854. |
| merged_mic_decoys_j | float | high | Probability from sub-model trained on MIC measurements merged across 4 ChEMBL assays (cutoff 10 uM; n=1070 incl. decoys). Recommended threshold: 0.883. |
| merged_mic_decoys_f | float | high | Probability from sub-model trained on MIC measurements merged across 7 ChEMBL assays (cutoff 10 uM; n=1010 incl. decoys). Recommended threshold: 0.866. |
| merged_mic_decoys_d | float | high | Probability from sub-model trained on MIC measurements merged across 6 ChEMBL assays (cutoff 10 uM; n=970 incl. decoys). Recommended threshold: 0.893. |
| merged_mic_decoys_k | float | high | Probability from sub-model trained on MIC measurements merged across 6 ChEMBL assays (cutoff 10 uM; n=950 incl. decoys). Recommended threshold: 0.877. |

_10 of 28 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos5eya.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos5eya.zip)

### Resource Consumption
- **Model Size (Mb):** `450`
- **Environment Size (Mb):** `1888`


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
