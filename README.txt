Kaggle APC Case: Car Price Prediction
Project Description
This project involves developing a predictive model for the final sale price of used vehicles in Spain. The dataset used is “Used Cars Prices in Spain”, which contains 23 explanatory features and 1 target variable (Price). The primary objective is to accurately predict the realistic price of a vehicle and identify which technical, commercial, and usage attributes most significantly influence this market value.

Authors and Affiliation
Marc Dalmau Guamis – 1710713

Alejandro Flores Hernández – 1709458 
Universitat Autònoma de Barcelona (UAB) – Course: Machine Learning – Group 07

Project Structure
Cars_Data_6k.csv: Original vehicle dataset.

model_cotxes.ipynb: Notebook containing analysis, preprocessing, and modeling.

Data Preprocessing
Missing Values (NaNs):

Removal of the Tank column (100% empty).

Imputation of numerical variables using KNNImputer after standardization with StandardScaler.

Imputation of the categorical variable Sticker using the mode.

Imputation of the Location variable using a manual categorical KNN approach.

Categorical Variable Encoding:

One-Hot Encoding (OHE): Sticker, Fuel, Transmission.

Target Encoding with Cross-Validation (K-Fold): Brand, Name, Location.

Scaling: All numerical variables were scaled using StandardScaler to improve the numerical stability of the models.

Metric Selection
As this is a regression problem, two primary metrics were used:

MSE (Mean Squared Error): Penalizes large errors and is useful for stable model comparison.

MAPE (Mean Absolute Percentage Error): Expresses the relative error as a percentage of the actual value, facilitating practical interpretation.

Model Selection and Training
Initially, several regression algorithms were tested: linear models, decision trees, ensembles, and non-linear approaches.

Phase 1: Models with very high errors or unstable predictions were discarded.

Phase 2: Models showing overfitting (high training performance but poor test performance) were removed.

Remaining Models: Applied Sequential Feature Selection to choose the most relevant variables for each model.

Final Model: An Optimized Random Forest using hyperparameter tuning (GridSearchCV).

Final Results:

CV MSE: 582,990.37

CV MAPE: 1.36%

Test MSE: 851,623.23

Test MAPE: 1.68%

Final Analysis and Practical Applications
The final model is stable and accurate, with predictions closely aligned with real market prices. Practical applications include:

Dealerships looking to set fair prices without overpaying.

Mass-purchase companies identifying undervalued cars with high profit potential.

Sales platforms needing to recommend competitive prices automatically.

Consumers wanting to verify if an advertisement price is fair.

Technologies and Libraries Used
Python 3.x

Libraries: pandas, numpy, scikit-learn, matplotlib

Others: Jupyter Notebook for experimentation and Tau-class LaTeX template for the final report.

Execution
Clone the public repository: git clone https://github.com/marcdalg05/CasKaggle.git

Setup environment and dependencies: python -m venv venv source venv/bin/activate pip install -r requirements.txt

Generate report (Optional): pdflatex report/main.tex

License
This project is public and can be used under the CC-BY 4.0 license, citing the original authors.

