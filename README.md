# Volatility in Exoplanet Habitability Classification Under Measurement Uncertainty

## Overview
This project introduces a volatility-based framework for evaluating the stability of exoplanet habitability classifications under measurement uncertainty. Using data from the NASA Exoplanet Archive, the analysis examines how small perturbations in planetary and stellar features impact classification outcomes. The approach combines traditional classification models with Monte Carlo sampling to quantify prediction sensitivity, providing a complementary perspective to standard performance metrics such as accuracy, precision, and recall.

## Project Structure

### Data
This project uses data from the NASA Exoplanet Archive planetary systems dataset. The dataset includes planetary and stellar characteristics along with associated measurement uncertainties.
- **`exoplanet_volatility_cleaned.csv`**: Cleaned dataset used for modeling, containing selected planetary and stellar features, derived uncertainty measures, and the proxy habitability label

### Files
- **`Data Preprocessing.ipynb`**: Cleans and filters the raw NASA Exoplanet Archive dataset, selects relevant features, handles missing values, constructs uncertainty measures from asymmetric error bounds, and defines the proxy habitability label
- **`Modeling.ipynb`**: Implements classification models (logistic regression and random forest), evaluates performance, and performs Monte Carlo perturbation to compute volatility scores for each observation

### Reports
- **`Exoplanet_Volatility.pdf`**: Full academic paper detailing background, methodology, results, and discussion of the volatility framework

## Methodology
The project followed these main steps:
1. **Data Preprocessing**: Filtered the dataset to include only default parameter sets, selected key planetary and stellar features, handled missing values, and constructed uncertainty measures from reported error bounds
2. **Proxy Habitability Definition**: Defined a binary habitability label using thresholds on planetary radius and equilibrium temperature
3. **Model Training**: Trained logistic regression and random forest models using a 70/30 train-test split, with class weighting applied to address imbalance
4. **Model Evaluation**: Assessed performance using accuracy, precision, recall, and F1 score
5. **Volatility Analysis**: Applied Monte Carlo perturbations using uncertainty-informed sampling to measure classification stability for each exoplanet

## Key Results
- **Class Imbalance**: The dataset contained 1,483 observations, with only 9 classified as proxy-habitable
- **Logistic Regression**: Achieved perfect recall (1.00) but low precision (0.094), indicating strong sensitivity to rare cases but higher false positives
- **Random Forest**: Achieved high accuracy (0.998), perfect precision (1.000), and moderate recall (0.667), demonstrating more conservative but precise predictions
- **Volatility Analysis**: Most observations exhibited low volatility, but certain planets showed significant instability under perturbation, indicating sensitivity near classification boundaries
- **Uncertainty Relationship**: Higher measurement uncertainty was associated with increased prediction instability

## Installation

### Project Setup
To run this project locally, download the required dataset and notebooks.

**Dataset**
The dataset is derived from the NASA Exoplanet Archive planetary systems table. Due to file size constraints, the dataset is not included in this repository.

To obtain the data:
1. Visit: https://exoplanetarchive.ipac.caltech.edu/
2. Navigate to the **Planetary Systems (PS) table**
3. Download the dataset as a CSV file
4. Save the file locally

**Notebooks**
- Data Preprocessing.ipynb  
- Modeling.ipynb  

Place all files in the same directory before running the notebooks.

### Install Required Libraries
Ensure Python 3 is installed, then install the required libraries:

```bash
pip install numpy pandas matplotlib scikit-learn jupyter
