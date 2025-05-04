# Beyond sporadic outbreaks: Classifying and explaining dengue endemicity over scenarios of global change

This notebook presents code for classifying and predicting dengue virus (DENV) endemicity status at the national level using machine learning models trained on ecological and socioeconomic predictors.

## Installation
At the top of the notebook, there is a line that must first be run to ensure all dependencies are installed:
`pip install -r requirements.txt` 

## Running the code
As long as you have installed all necessary requirements, the code should run correctly by selecing "Run all". 

## Project structure
```plaintext
data/                         # Raw and processed input datasets
output/                       # Outputs directory
├── data/                     # Model outputs, predictions, and intermediate results
└── figures/                  # Plots and maps (e.g., predicted incidence maps)
src/                          # Scripts and helper functions
├──classify_predict_endemicity_status.ipynb  # Main analysis notebook
```

## Workflow

The workflow includes:

1. **Label Creation**  
   Uses k-means and meanshift clustering on dengue incidence time series to generate endemicity labels for each country.

2. **Endemicity Classification**  
   Logistic regression model (with/without SGD) trained using ecological and socioeconomic features to classify countries as non-endemic, hypo-endemic, or endemic.

3. **Incidence Prediction**  
   A separate regression model predicts log-transformed dengue incidence per 100k population using the same features. Confidence intervals are calculated for predictions in future years.
   
4. **Visualization**  
   Predicted incidence for 2023 is visualized in a choropleth map.

5. **Interpretability**  
   SHAP (SHapley Additive exPlanations) is used to interpret the contribution of individual features to model predictions.
