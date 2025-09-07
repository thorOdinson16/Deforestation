# Fire Type Classifier: AI-Driven Fire Detection from MODIS Data

## Overview

Fire Type Classifier is a machine learning-powered application that predicts fire types using MODIS satellite data. It processes fire data from CSV files (2021.csv, 2022.csv, 2023.csv), trains and evaluates multiple classifiers, and provides an interactive Streamlit interface for real-time fire type predictions. The app classifies fires into categories such as Vegetation Fire, Other Static Land Source, and Offshore Fire based on features like brightness, fire radiative power (FRP), and confidence levels.

## Key Features

- **Data Processing**: Combines and analyzes fire data from 2021-2023, handling missing values and class imbalances using SMOTE.
- **Model Training**: Trains multiple models (Logistic Regression, Decision Tree, Random Forest, KNN) and selects the best-performing model (Random Forest) based on accuracy.
- **Feature Scaling**: Uses StandardScaler to preprocess input features for consistent model performance.
- **Interactive Prediction**: Streamlit app allows users to input satellite readings (brightness, bright_t31, FRP, scan, track, confidence) to predict fire types.
- **Model Persistence**: Saves the trained model and scaler for deployment using joblib.

## Tech Stack

- **Data Processing**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn
- **Machine Learning**: Scikit-learn (models, preprocessing, metrics), imbalanced-learn (SMOTE)
- **Frontend**: Streamlit
- **Model Storage**: joblib
- **Dependencies**: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `imbalanced-learn`, `streamlit`, `joblib`

## File Structure

- `app.py`: Streamlit application for real-time fire type predictions using the trained model.
- `main.ipynb`: Jupyter Notebook for data processing, exploratory data analysis (EDA), model training, and evaluation.
- Input CSVs: `2021.csv`, `2022.csv`, `2023.csv` (fire data from MODIS satellite readings).

## Getting Started

### Prerequisites
- Python 3.10 or higher
- Jupyter Notebook (for running `main.ipynb`)
- Streamlit
- pip for installing dependencies

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/fire-type-classifier.git
   ```
2. Navigate to the project directory:
   ```bash
   cd fire-type-classifier
   ```
3. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn streamlit joblib
   ```
   Alternatively, create a `requirements.txt` with the above packages and run:
   ```bash
   pip install -r requirements.txt
   ```

### Data Requirements
- Ensure `2021.csv`, `2022.csv`, and `2023.csv` are in the project directory. These files should contain MODIS fire data with columns like `brightness`, `bright_t31`, `frp`, `scan`, `track`, `confidence`, and `type`.

### Training the Model
1. Open `main.ipynb` in Jupyter Notebook.
2. Run all cells to:
   - Load and combine CSV data.
   - Perform EDA (check data structure, missing values, duplicates).
   - Apply SMOTE for class imbalance.
   - Train and evaluate models (Logistic Regression, Decision Tree, Random Forest, KNN).
   - Save the best model (`best_fire_detection_model.pkl`) and scaler (`scaler.pkl`).

### Running the App
1. Launch the Streamlit app:
   ```bash
   streamlit run app.py
   ```
2. Access the app in your browser (typically at `http://localhost:8501`).

## How to Use

1. **Train the Model**:
   - Run `main.ipynb` to process the input CSVs and generate the trained model and scaler files.
2. **Predict Fire Type**:
   - Open the Streamlit app.
   - Enter MODIS satellite readings:
     - Brightness (e.g., 300.0)
     - Bright_t31 (e.g., 290.0)
     - Fire Radiative Power (FRP) (e.g., 15.0)
     - Scan (e.g., 1.0)
     - Track (e.g., 1.0)
     - Confidence Level (low, nominal, high)
   - Click "Predict Fire Type" to view the predicted fire type (e.g., Vegetation Fire, Other Static Land Source, Offshore Fire).

## Future Enhancements

- Integrate real-time MODIS data via APIs for live predictions.
- Support additional fire types or advanced models like XGBoost.
- Add visualizations in the Streamlit app for input data trends.
- Deploy the app to cloud platforms like Streamlit Cloud or Heroku.