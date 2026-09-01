# AquaTwin-Safe

AquaTwin-Safe is a cyber-secure digital-twin framework for resilient water-management systems. This repository provides the reproducible anomaly-detection experiments reported in the associated research manuscript.

## Implemented Models

The experimental evaluation includes:

- Isolation Forest
- Dense Autoencoder
- LSTM Autoencoder

## Dataset

The experiments use the BATADAL benchmark based on the C-Town water-distribution network.

The original datasets are not redistributed in this repository. They can be obtained from the official Singapore University of Technology and Design iTrust dataset portal:

https://www.sutd.edu.sg/itrust/itrust-labs/datasets/dataset-characteristics/batadal

## Experimental Configuration

- Number of SCADA variables: 43
- LSTM sequence window: 24 hours
- Random seed: 42
- Dense Autoencoder threshold: 99th percentile
- LSTM Autoencoder threshold: 97.5th percentile
- Evaluation dataset: Official BATADAL test dataset

## Main Results

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC | PR-AUC |
|---|---:|---:|---:|---:|---:|---:|
| Isolation Forest | 0.7841 | 0.3136 | 0.0909 | 0.1410 | 0.5570 | 0.2628 |
| Dense Autoencoder | 0.8559 | 0.8354 | 0.3243 | 0.4673 | 0.8055 | 0.6157 |
| LSTM Autoencoder | 0.8548 | 0.6754 | 0.5061 | 0.5787 | 0.8537 | 0.5602 |

The LSTM Autoencoder achieved the highest F1-score and ROC-AUC. It also raised at least one alert within all seven labelled attack events. The Dense Autoencoder achieved the highest precision and PR-AUC.

## Repository Structure

```text
AquaTwin-Safe/
├── notebooks/
│   └── BATADAL_Experiment_01.ipynb
├── results/
│   ├── final_three_model_comparison.csv
│   ├── auc_comparison.csv
│   ├── experiment_summary.txt
│   └── experimental figures
├── requirements.txt
├── README.md
└── LICENSE
```

## Installation

Create a Python virtual environment and install the required packages:

```bash
pip install -r requirements.txt
```

## Reproducing the Experiment

1. Download the BATADAL datasets from the official source.
2. Create a local data directory.
3. Place the downloaded datasets in the data directory.
4. Update the dataset paths inside the notebook.
5. Install the packages listed in `requirements.txt`.
6. Open `notebooks/BATADAL_Experiment_01.ipynb`.
7. Run the notebook cells in chronological order.

## Methodological Safeguards

The experimental procedure follows these safeguards:

- The scaler is fitted only on normal training data.
- Test data are excluded from model training.
- Detection thresholds are derived from normal validation errors.
- The official test dataset is used for final reporting.
- Temporal order is preserved during LSTM training.
- Continuous anomaly scores are used for ROC-AUC and PR-AUC evaluation.

## Code and Results Availability

The experiment notebook, environment requirements, generated predictions, performance tables and figures are publicly available in this repository.

Repository:

https://github.com/MueenCh/AquaTwin-Safe

## Citation

Please cite the archived software release as:

Mueen ud Din (2026). *AquaTwin-Safe: Reproducible Temporal Anomaly Detection for Cyber-Secure Water Digital Twins* (Version 1.0.0). Zenodo. https://doi.org/10.5281/zenodo.22226196

## Author

**Mueen ud Din**  
PhD Scholar  
Department of Computer Science  
Riphah International University, Pakistan  
Email: mueen80@gmail.com

## Funding

The author received no specific funding for this research.

## Conflict of Interest

The author declares no competing interests.

## License

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.22226196.svg)](https://doi.org/10.5281/zenodo.22226196)

**Permanent software DOI:** https://doi.org/10.5281/zenodo.22226196

This repository is intended for academic research and reproducibility. See the `LICENSE` file for usage conditions.
