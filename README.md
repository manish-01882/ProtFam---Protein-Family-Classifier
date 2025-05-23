# ProtFam - Protein Family Classifier

A full-stack web application for predicting proteins near into their respective families based on physicochemical properties. The application uses machine learning to predict protein families and provides both single-protein analysis and bulk classification capabilities.

## Features

- **Single Protein Analysis**: Interactive interface for analyzing individual proteins
- **Bulk Analysis**: Process multiple proteins through CSV upload
- **Visualization**: Interactive charts showing prediction probabilities and feature importance
- **Downloadable Results**: Export classification results as CSV files

## Installation

### 1. Create a Virtual Environment

It's recommended to use a virtual environment to manage dependencies:

```bash
# Create a virtual environment
python -m venv venv

# Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

## Usage

### Starting the Backend Server

```bash
# Start the FastAPI backend server
uvicorn backend:app --reload
```

The backend API will be available at `http://localhost:8000`.

### Starting the Frontend

```bash
# Start the Streamlit frontend
streamlit run frontend.py
```

The frontend will be available at `http://localhost:8501`.

## Input Parameters

### Basic Properties
- Nneg: Number of Negative Charged Residues
- Npos: Number of Positive Charged Residues
- Exc1: Excitation Coefficient 1
- Exc2: Excitation Coefficient 2
- I.Index: Instability Index
- A.Index: Aliphatic Index

### Advanced Properties
- GRAVY: Grand Average of Hydropathicity
- Ser: Serine Count
- Thr: Threonine Count
- Tyr: Tyrosine Count
- ExpAA: Expected AAs in Sequence
- PredHel: Predicted Transmembrane Helices

### Tools used to get above params
- Nneg, Npos, Exc1, Exc2, I_Index, A_Index, GRAVY, Ser, Thr, Tyr - Expasy ProtParam
- ExpAA, PredHel - THMMM by DTU

## Bulk Analysis

For bulk analysis, prepare a CSV file with the following columns:
- Nneg, Npos, Exc1, Exc2, I_Index, A_Index, GRAVY, Ser, Thr, Tyr, ExpAA, PredHel

The application will process the file and provide a downloadable CSV with predictions.

## Model Information

The application uses a Random Forest Classifier trained on protein physicochemical properties to predict protein families. The model can classify proteins into the following families:
- DNA Repair Protein
- Decarboxylase
- Defensin
- Heat Shock Protein
- RNA Binding Protein
- Voltage Gated Channel

## Technologies Used

- **Frontend**: Streamlit
- **Backend**: FastAPI
- **Machine Learning**: scikit-learn
- **Data Processing**: Pandas
- **Visualization**: Plotly

## Application Outputs

The application generates several visualization outputs to help understand the classification results:

### Individual Analysis
- **Frontend Interface**: Interactive interface for single protein analysis
![Individual Analysis Frontend](outputs/Individual%20Analysis%20-%20Frontend.png)

- **Classification Results**: Visual representation of prediction probabilities
![Individual Analysis Classification](outputs/Individual%20Analysis%20-%20Classification.png)

- **Feature Importance**: SHAP-based visualization showing the importance of each feature
![Individual Analysis Feature Importance](outputs/Individual%20Analysis%20-%20Feature%20Importance.png)

### Bulk Analysis
- **Upload and Preview**: Interface for uploading and previewing CSV files
![Bulk Analysis Upload and Preview](outputs/Bulk%20Analysis%20-%20Upload%20and%20Preview.png)

- **Predictions and Download**: Results visualization with CSV download option
![Bulk Analysis Predictions and Download](outputs/Bulk%20Analysis%20-%20Predictiona%20and%20CSV%20Download.png)

### Model Interpretability
- **SHAP Implementation**: Detailed SHAP analysis showing feature contributions to predictions
![SHAP Implementation](outputs/Shap%20Implementation%20in%20Protein%20Family%20Classifer%20Model.png)

All outputs are saved in the `outputs` directory for reference and analysis.
 
