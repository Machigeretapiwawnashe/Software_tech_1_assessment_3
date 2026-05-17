# Software_tech_1_assessment_3
# Macroinvertebrate Image Analysis System

## Project Goal
A modular Python application that indexes a macroinvertebrate image dataset,
performs exploratory data analysis, and feeds into a classification pipeline.

## Features
- Dataset indexing with metadata extraction (label, width, height, channels)
- Class distribution analysis
- Image size distribution analysis
- Sample image grid visualisation
- Dataset summary statistics
- Image preprocessing with resizing, normalisation, and label encoding
- Macroinvertebrate image classification using Random Forest or SVM
- Model evaluation with confusion matrix and per-class accuracy charts
- Stage 3 console deployment for model reuse and live image prediction

## Packages Used
- `pandas` — tabular data management and indexing
- `numpy` — numerical operations
- `opencv-python` — image reading and metadata extraction
- `matplotlib` / `seaborn` — EDA and evaluation visualisations
- `pillow` — image support utilities
- `scikit-learn` — machine learning classification and evaluation metrics
- `joblib` — model persistence (save and load trained classifier)

## Installation
1. Create and activate a virtual environment:
```bash
   python -m venv .venv
   source .venv/bin/activate   # Windows: .venv\Scripts\activate
```
2. Install dependencies:
```bash
   pip install -r requirements.txt
```

## Dataset Setup
The project requires the Kaggle Stream Macroinvertebrates image dataset. To set up the data:

1. **Download the dataset** from Kaggle:
   - Visit: https://www.kaggle.com/datasets/stream-macroinvertebrates (or the specific dataset link if different)
   - Download the dataset to your local machine

2. **Place the data in the correct location**:
   - Extract the downloaded dataset
   - Copy all class folders (e.g., `Asellus sp/`, `Baetidae sp/`, `Elmis sp/`, etc.) into the `data/raw/` directory
   - The final structure should look like:
     ```
     macro_project/
     └── data/
         └── raw/
             ├── Asellus sp/
             ├── Baetidae sp/
             ├── Elmis sp/
             └── ... (all other class folders)
     ```

3. **Verify setup**: Once data is placed, you can run the full pipeline to process and analyze the dataset.

## How to Run
The top-level interactive interface is launched with:
```bash
python run.py
```
This menu includes:
- option 1: run the full pipeline (Stage 1 + Stage 2)
- option 2: classify a single new image using the saved model
- option 3: select classes and classify either one image or the entire selected class set
- option 4: inspect output directories

If you want to run just the pipeline without the menu, use:
```bash
python main.py
```

A Stage 3 console deployment interface is also available directly via:
```bash
python stage3.py
```

EDA outputs are saved to `outputs/eda/`.
The trained model and evaluation charts are saved to `outputs/models/`.

## Implementation Summary
An implementation summary is available in `IMPLEMENTATION_SUMMARY.md`.

## Folder Structure
macro_project/
├── data/raw/                    # Place dataset here
├── outputs/eda/                 # EDA charts saved here
├── outputs/models/              # Trained model and evaluation charts saved here
├── src/
│   ├── config.py
│   ├── main.py
│   ├── models/records.py
│   └── services/
│       ├── dataset_indexer.py
│       ├── eda_service.py
│       ├── preprocessor.py
│       ├── classifier_service.py
│       └── model_evaluator.py
├── MANUAL_TESTING.md
├── README.md
└── requirements.txt
