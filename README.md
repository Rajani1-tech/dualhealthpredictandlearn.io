# Multiple Disease Prediction System

## Overview

A web application for predicting multiple diseases using machine learning. The system includes user authentication, prediction tracking, and disease analysis visualizations. It predicts Heart Disease, Diabetes, and Breast Cancer using custom machine learning implementations.

## Features

- User authentication with secure password hashing
- Three disease prediction models (Heart Disease, Diabetes, Breast Cancer)
- Prediction history tracking for each user
- Exploratory Data Analysis visualizations
- Model performance metrics and confusion matrices
- Health alerts for repeated predictions
- Interactive web interface with Streamlit

## Project Structure

```
Multiple-Disease-Prediction/
├── app.py                          
├── plot_metric.py                 
├── requirements.txt               
├── README.md                       
│
├── data/
│   ├── raw/                       
│   │   ├── diabetes.csv
│   │   └── heart.csv
│   └── processed/                 
│       ├── X_train.npy
│       ├── X_test.npy
│       ├── X_val.npy
│       ├── y_train.npy
│       ├── y_test.npy
│       └── y_val.npy
│
├── database/                      
│
├── notebooks/                    
│   ├── eda/                     
│   │   ├── eda_diabetic.ipynb
│   │   └── eda_heart_disease.ipynb
│   └── experiments/              
│
├── results/                      
│   ├── eda/                      
│   │   ├── diabetes/
│   │   ├── heart_disease/
│   │   └── breast_cancer/
│   ├── metrics/                  
│   │   └── diabetic_model_metrics.csv
│   ├── plots/                   
│   └── static/                  
│       ├── diabetes/
│       ├── heart_disease/
│
├── saved_models/                
│   ├── diabetes_model_decision_tree.sav
│   ├── weights.npy             
│   └── bias.npy                 
│
├── src/                          
│   ├── __init__.py
│   │
│   ├── app/                      
│   │   ├── __init__.py
│   │   ├── main.py             
│   │   └── pages/               
│   │       ├── __init__.py
│   │       ├── diabetes_page.py
│   │       ├── heart_page.py
│   │       └── breast_cancer_page.py
│   │
│   ├── auth/                     
│   │   ├── __init__.py
│   │   └── user.py              
│   │
│   ├── config/                  
│   │   ├── __init__.py
│   │   └── settings.py          
│   │
│   ├── models/                   
│   │   ├── __init__.py
│   │   ├── decision_tree.py     
│   │   ├── logistic_regression.py 
│   │   └── svm.py               
│   │
│   ├── training/                 
│   │   ├── __init__.py
│   │   ├── train_diabetes.py    
│   │   └── train_heart.py      
│   │
│   └── utils/                    
│       ├── __init__.py
│       ├── visualization.py     
│       ├── database.py          
│       ├── data_preprocessing.py 
│       └── model_evaluation.py  

    
```

## Technologies Used

- Python: Core programming language
- Streamlit: Web application framework
- NumPy: Numerical computations
- Pandas: Data manipulation
- Scikit-learn: ML preprocessing and metrics
- Matplotlib and Seaborn: Data visualization
- SQLite: User database
- PIL: Image processing

## Datasets

### Heart Disease Dataset
Features: 13 attributes including age, sex, chest pain type, blood pressure, cholesterol, ECG results, and more

### Diabetes Dataset
Features: 8 attributes including pregnancies, glucose level, blood pressure, BMI, insulin, and age

### Breast Cancer Dataset
Features: 30 attributes reduced to 10 principal components using PCA

## Machine Learning Models

### 1. Heart Disease - Logistic Regression
- Custom implementation using gradient descent
- Learning rate: 0.01
- Epochs: 1000
- Activation: Sigmoid function

### 2. Diabetes - Decision Tree
- Custom implementation with Gini impurity
- Binary tree with recursive splitting
- Input validation for data quality

### 3. Breast Cancer - Support Vector Machine (SVM)
- Custom SVM implementation with hinge loss
- PCA dimensionality reduction (30 to 10 features)
- L2 regularization for preventing overfitting

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/asmriti/Multiple-Disease-Prediction.git
   cd Multiple-Disease-Prediction
   ```

2. Create and activate virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Run the application:
   ```bash
   streamlit run app.py
   ```

2. Open browser to: http://localhost:8501

3. Create an account or login

4. Select disease prediction from sidebar

5. Fill in medical parameters and get prediction

## Key Modules

### app.py
Main entry point. Handles:
- User authentication (signup/login)
- Navigation menu
- Page routing to disease prediction pages
- Prediction history display

### src/app/pages/
Individual disease prediction interfaces:
- diabetes_page.py: Diabetes prediction with 8 input fields
- heart_page.py: Heart disease prediction with 13 input fields
- breast_cancer_page.py: Breast cancer prediction with 10 PCA features

### src/auth/user.py
User management:
- User registration and login
- Password hashing with SHA-256
- Prediction history storage
- Recent prediction checking for health alerts

### src/models/
Custom ML implementations:
- decision_tree.py: Custom Decision Tree classifier
- logistic_regression.py: Custom Logistic Regression
- svm.py: Custom SVM with PCA support

### src/training/
Model training scripts:
- train_diabetes.py: Trains Decision Tree on diabetes data
- train_heart.py: Trains Logistic Regression on heart data

### src/utils/
Utility functions:
- data_preprocessing.py: Data normalization and splitting
- model_evaluation.py: Model evaluation and metrics
- visualization.py: Plotting and chart generation
- database.py: Database operations

## Database Schema

### Users Table
- email (PRIMARY KEY)
- username (UNIQUE)
- password (SHA-256 hashed)

### User Predictions Table
- id (PRIMARY KEY)
- email (FOREIGN KEY)
- disease
- input_parameters (JSON)
- prediction_result
- timestamp

## Features Explained

### User Authentication
Users can sign up and login securely. All predictions are stored with user email.

### Prediction History
View all past predictions with timestamps and input parameters.

### Health Alerts
System warns if user gets 3+ positive predictions for same disease within 30 days.

### Model Performance
Each model page shows:
- Confusion matrix
- Accuracy metrics
- Precision, Recall, F1-Score

### EDA Visualizations
Jupyter notebooks in notebooks/eda/ provide detailed data analysis.

## Requirements

```
numpy==1.26.3
scikit-learn==1.3.2
streamlit==1.29.0
streamlit-option-menu==0.3.6
```


## Acknowledgments

- Heart Disease Dataset: Kaggle
- Diabetes Dataset: Publicly available medical datasets
- Breast Cancer Dataset: Wisconsin Breast Cancer Dataset (scikit-learn)
- Scikit-learn library for machine learning utilities

