# Healthcare Analytics — MS Thesis Implementation

Original implementation and results for the MS Software Engineering thesis
**"Integrating Fine-Tuned LLAMA Models for Healthcare"** (multi-method healthcare
data analysis based on modeling, machine learning, and patient segmentation), by
Ahmad Mukhtiar, Department of Software Engineering, Government College University
Faisalabad.

This repository contains the thesis **code, results, and figures** so the work can be
inspected and reproduced. It does **not** contain the thesis document or presentation
slides.

## What the pipeline does

The notebook (`notebook/Med.ipynb`) implements a six-stage analytical pipeline on a
large healthcare dataset (~55,500 patient records):

1. **Stage 1 — Exploratory data analysis:** distributions of age, gender, blood type,
   medical condition, admission type, billing, and length of stay.
2. **Stage 2 — Preprocessing & feature engineering:** cleaning, categorical encoding,
   and derivation of Length of Stay (discharge − admission).
3. **Stage 3 — Statistical analysis:** descriptive statistics, correlation analysis,
   and cost-by-condition / cost-by-admission-type analysis.
4. **Stage 4 — Machine learning:** Decision Tree, Random Forest, Logistic Regression,
   and K-Nearest Neighbours for predicting medical test results, with accuracy,
   confusion matrices, and Random Forest feature importance.
5. **Stage 5 — Patient segmentation:** K-Means clustering (k = 3) with PCA
   visualisation and cluster feature profiling.
6. **Stage 6 — Summary & insight generation:** consolidated cluster and model
   summaries (foundation for the LLM-based interpretation layer described in the thesis).

## Dataset

The dataset is the publicly available **"Healthcare Dataset"** on Kaggle:
- https://www.kaggle.com/datasets/prasad22/healthcare-dataset

It is a synthetic dataset created for learning/demonstration purposes. Download
`healthcare_dataset.csv` from the link above and place it in a `data/` folder (or beside
the notebook), then update the input path in the first cells of `Med.ipynb` if needed.

> Note: the raw and processed CSV files are intentionally not committed (see `.gitignore`);
> download the dataset from Kaggle and run the notebook to regenerate all outputs.

## Requirements

```bash
pip install -r requirements.txt
```
(`pandas`, `numpy`, `scikit-learn`, `matplotlib`, `jupyter`)

## How to reproduce

```bash
# 1. Download healthcare_dataset.csv from the Kaggle link above into ./data/
# 2. Launch the notebook
jupyter notebook notebook/Med.ipynb
# 3. Run all cells top to bottom
```

Running the notebook regenerates the processed dataset and writes the figures
(`figures/Stage1..Stage6/`), the XML result files (`results/xml/Stage1..Stage6/`), and
the report summaries (`results/reports/`).

## Repository layout

```
.
├── README.md
├── requirements.txt
├── LICENSE
├── notebook/
│   └── Med.ipynb                # full six-stage pipeline
├── figures/                     # generated figures, by stage
│   └── Stage1 ... Stage6/
└── results/
    ├── xml/Stage1 ... Stage6/   # numerical results (descriptive stats, correlations,
    │                            #   ML metrics, cluster profiles, insights)
    └── reports/                 # pipeline overview, figure captions, summaries
```

## Notes

- Results are deterministic where random seeds are set in the notebook.
- This repository reflects the original thesis implementation as submitted; the dataset
  is synthetic, so the analysis is a methodological demonstration of the pipeline rather
  than a source of clinical conclusions.
