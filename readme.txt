# Cas Kaggle APC: Predicció Preu Cotxe

## Descripció del projecte

Aquest projecte consisteix en el desenvolupament d’un model de predicció del preu final de venda de vehicles d’ocasió a Espanya.  
S’ha treballat amb la base de dades **“Used Cars Prices in Spain”**, que conté 23 atributs explicatius i 1 variable objectiu (`Price`).  

L’objectiu principal és predir de manera precisa el preu realista d’un vehicle i identificar quins atributs tècnics, comercials i d’ús influeixen més en aquest valor de mercat.

---

## Autors i afiliació

- **Marc Dalmau Guamis** – 1710713  
- **Alejandro Flores Hernández** – 1709458  

**Universitat Autònoma de Barcelona (UAB) – Assignatura: Aprenentatge Computacional – Grup 07**

---

## Estructura del projecte

Cars_Data_6k.csv # Dataset original de vehicles
model_cotxes.ipynb # Notebook amb l’anàlisi, preprocesament i modelatge

## Preprocessament de dades

- **Valors buits (NaNs)**:  
  - Eliminació de la columna `Tank` (100% buida).  
  - Imputació de variables numèriques amb `KNNImputer`, després d’estandarditzar-les amb `StandardScaler`.  
  - Imputació de la variable categòrica `Sticker` amb la moda.  
  - Imputació de la variable `Location` amb un KNN categòric manual.  

- **Codificació de variables categòriques**:  
  - **One-Hot Encoding (OHE)**: `Sticker`, `Fuel`, `Transmission`.  
  - **Target Encoding amb validació creuada (K-Fold)**: `Brand`, `Name`, `Location`.  

- **Escalat**: Totes les variables numèriques es van escalar amb `StandardScaler` per millorar l’estabilitat numèrica dels models.

---

## Selecció de mètriques

Com es tracta d’un problema de regressió, es van utilitzar dues mètriques principals:  

- **MSE (Mean Squared Error)**: penalitza errors grans i és útil per comparar models de manera estable.  
- **MAPE (Mean Absolute Percentage Error)**: expressa l’error relatiu en percentatge respecte al valor real, facilitant la interpretació pràctica.  

Aquestes dues mètriques combinades proporcionen una visió completa de l’error del model.

---

## Selecció i entrenament de models

1. Inicialment es van provar diversos algoritmes de regressió: models lineals, arbres de decisió, ensembles i aproximacions no lineals.  
2. Fase 1: es van descartar models amb errors molt alts o prediccions inestables.  
3. Fase 2: es van descartar models amb **overfitting** (alt rendiment en train però pobre en test).  
4. Models restants: aplicació de **Sequential Feature Selection** per escollir les variables més rellevants per a cada model.  
5. Model final seleccionat: **Random Forest optimitzat** amb cerca d’hiperparàmetres (`GridSearchCV`).  

**Resultats finals**:  
- CV MSE = 582990.37  
- CV MAPE = 1.36%  
- Test MSE = 851623.23  
- Test MAPE = 1.68%

---

## Anàlisi final i aplicacions pràctiques

El model final és estable i precís, amb prediccions molt properes als preus reals del mercat.  
Aplicacions pràctiques:  

- Concessionaris que volen establir preus justos sense pagar de més.  
- Empreses de compra massiva per identificar cotxes infravalorats amb potencial benefici.  
- Plataformes de venda que necessiten recomanar preus competitius automàticament.  
- Consumidors que volen verificar si un anunci és just.  

---

## Tecnologies i llibreries utilitzades

- **Python 3.x**  
- Llibreries: `pandas`, `numpy`, `scikit-learn`, `matplotlib`  
- Altres: `Jupyter Notebook` per a experiments i `Tau-class LaTeX template` per al document final  

Exemple de llibreries Python utilitzades:

```python
import pandas as pd
from sklearn.preprocessing import StandardScaler, LabelEncoder
from sklearn.metrics import mean_squared_error, mean_absolute_percentage_error
from sklearn.model_selection import train_test_split, cross_val_score, KFold, GridSearchCV
from sklearn.ensemble import RandomForestRegressor
import matplotlib.pyplot as plt
import numpy as np

## Execució

1. Clonar el repositori públic:

```bash
git clone https://github.com/marcdalg05/CasKaggle.git


python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
pip install -r requirements.txt

pdflatex report/main.tex


Llicència

Aquest projecte és públic i pot ser utilitzat sota la llicència CC-BY 4.0, citant els autors originals.


