# Beyond sporadic outbreaks: Classifying and explaining dengue endemicity over scenarios of global change

This notebook presents code for classifying and predicting dengue virus (DENV) endemicity status at the national level using machine learning models trained on ecological and socioeconomic predictors.

## Setup:

1. Enable Google Colaboratory as an app on your Google Drive account

2. Create a new Google Colab notebook, this will also create a "Colab Notebooks" directory under "MyDrive" i.e.
```
/content/drive/MyDrive/Colab Notebooks
```

3. Create the following directory structure in your Google Drive
```
/content/drive/MyDrive/Colab Notebooks/CPSC 381-581: Machine Learning/Final project
```

4. Move the classify_predict_endemicity.ipynb and requirements.txt into
```
/content/drive/MyDrive/Colab Notebooks/CPSC 381-581: Machine Learning/Final project/src
```
so that its absolute path is
```
/content/drive/MyDrive/Colab Notebooks/CPSC 381-581: Machine Learning/Final project/src/classify_predict_endemicity.ipynb
/content/drive/MyDrive/Colab Notebooks/CPSC 381-581: Machine Learning/Final project/src/requirements.txt
```

5. Prior to starting this project, please create a directory called 'data' within your 'Final project' directory with all files from the unzipped 'data' folder
```
/content/drive/MyDrive/Colab Notebooks/CPSC 381-581: Machine Learning/Exercises/data
```

6. Prior to starting this project, create a directory called 'output' within your 'Final project' directory with 'data' and 'figures' subfolders
```
/content/drive/MyDrive/Colab Notebooks/CPSC 381-581: Machine Learning/Exercises/output
/content/drive/MyDrive/Colab Notebooks/CPSC 381-581: Machine Learning/Exercises/output/data
/content/drive/MyDrive/Colab Notebooks/CPSC 381-581: Machine Learning/Exercises/output/figures
```


## Project structure
Prior to starting the project, confirm the project structure looks as follows, unzipping each folder and placing it in the correct location:
```plaintext
data/                         # Raw and processed input datasets
output/                       # Outputs directory
├── data/                     # Model outputs, predictions, and intermediate results
└── figures/                  # Plots and maps (e.g., predicted incidence maps)
src/                          # Scripts and helper functions
├──classify_predict_endemicity_status.ipynb  # Main analysis notebook
└──requirements.txt           # For installation, if desired
```

## Installation
At the top of the notebook, there is a line that can first be run to ensure all dependencies are installed:
`pip install -r requirements.txt` 
In Google Colab, all packages are pre-installed except for Country Converter. The import packages cell contains the necessary pip line to install this package as well - this will be faster than using requirements.txt, but it's there if necessary.

## Running the code
As long as you have installed all necessary requirements, the code should run correctly by selecing "Run all". 
NOTE: Data are pulled dynamically from Open Dengue and require an internet connection.
NOTE: If you are not using Google Colab, comment out the google.colab import, and uncomment the pip -requirements block directly below

## Workflow
The workflow includes:

1. **Label Creation**  
   Uses k-means and meanshift clustering on dengue incidence time series to generate endemicity labels for each country.

2. **Endemicity Classification**  
   Logistic regression model (with/without SGD) trained using ecological and socioeconomic features to classify countries as non-endemic, hypo-endemic, or endemic.

3. **Incidence Prediction**  
   A separate regression model predicts log-transformed dengue incidence per 100k population using the same features. Confidence intervals are calculated for predictions in future years.
   
4. **Forecasting**  
   Predicted incidence for 2023 is visualized in a choropleth map.

5. **Interpretability**  
   SHAP (SHapley Additive exPlanations) is used to interpret the contribution of individual features to model predictions.
