# Project

This repository aims to recreate a part of the energy simulation work conducted using EnergyPlus for my Master's thesis ([link here](https://etd.adm.unipi.it/t/etd-01262022-164701/)) with a newer version of En+ (from v8.9 --> 22.2). It utilizes a Python script to expedite, automate, and reduce errors in the process.


# Contents
```
   This repo contains:

- /#enplus_models        # with all the '.idf' files for the simulation in the city of Bolzano and Palermo
- /csv_outputs           # to store all the csv dataframes of the new results
- /images_outputs        # to store the outputs files as images
- Energy+.idd            # the input data dictionary of EnergyPlus v22.2
- *.epw files            # the weather files for the simulation in EnergyPlus
- my_thesis_with_.py     # the main file
- requirements.txt       # list of all libraries for the env
- OLD_total.xlsx         # with the KPIs'values of the thesis work to be compared
```

## Description

The purpose of this thesis work is to study the design and architectural integration of passive solar systems in residential and commercial buildings, considering not only energy efficiency but also environmental comfort, depending on the application context. The work is based on an extensive review of scientific literature and involves dynamic simulations, 3D modeling, evaluation of energy performance, and the associated level of comfort. Among the evaluations, rankings of the best combinations of passive solar systems have been compiled to catalog the most suitable ones for various circumstances.

The goal of this repository is to verify and expand upon a part of the thesis work regarding the initial simulations. The weaknesses of the thesis work include:
- High human error. The thesis work was carried out without the assistance of programs to automate lengthy repetitive processes.
- Lack of comparisons with a real case study adequately monitored.
- Use of outdated software compared to when the work was conducted.

The above-mentioned issues have been addressed, except for the comparison with a real case study. However, a comparison of the models to be simulated between the two versions of EnergyPlus used (8.9 and 22.2) was performed to verify whether the rankings previously compiled still hold.

# How to install and run

## Requirements
```
- Energyplus version 22.2 for Windows installed
- Python 3.*
- Install the required libraries
- Unzip the folders (if any)
```

# How to Use the File

The main function of the Python file has three input arguments: 
- run_files=None
- add_output=None
- collect_kpi=None

If you add "run_files," the simulation of all models within the #enplus_models folder will be executed. If you add "add_output," you can include an output variable at a specific position in the IDF file. If you add "collect_kpi," CSV files will be created inside the 'csv_outputs' folder.

The Python script performs the following actions:
- Initialization: The script starts with some import statements and variable declarations. It imports required libraries like matplotlib, os, pandas, re, and classes like IDF from the eppy.modeleditor module. It also sets the version number (enplus_vers) and defines some base case identifiers.
- Common Functions: This section contains utility functions used in the main script. Some of these functions include searching for files with specific extensions in a directory, generating directories based on combinations of values, renaming files and folders, adding output lines to IDF files, and calculating percentage differences between values.
- Main Function: The main function orchestrates the entire script's execution. It performs the following tasks:
  a. Search for IDF files in the root folder.
  b. Optionally add output lines to all IDF files to retrieve specific simulation results.
  c. Optionally run all IDF files using EnergyPlus with different weather files (Bolzano and Palermo).
  d. Search for ESO files (EnergyPlus output) generated by the simulations.
  e. Optionally collect key performance indicators (KPIs) such as total cooling and heating loads from ESO files.
  f. Compare the KPIs with previous results from an old Excel file and calculate percentage differences and rankings.
  g. Generate styled DataFrames and export the results to CSV and HTML files.
  h. Export the DataFrame as an image (png).



# Results

The first image is a heatmap of the percentage difference between the values of total annual energy consumption (AT, annual total) of the old EnergyPlus (8.9) and the new one (22.2). This is used to gain an initial overview of the results and identify patterns and errors. In the image, you can observe differences in Sunspace Trombes (ST) and in some individual cases. The difference compared to the values of the old EnergyPlus is < 1.5%, demonstrating excellent results.


![Alt Text](images_outputs/Distance % Heatmap En+ 22.2-8.9.png) 

### Rankings
In the ranking of the best combinations of annual heating (AH), the top combinations remain the same but in different positions.

![Alt Text](images_outputs/df_topAH_comp.png) 

In the ranking of the best combinations of annual total energy (AT), the ranking remains unchanged.

![Alt Text](images_outputs/df_topAT_comp.png) 

# Improvements

Future improvements could include:
- Code optimization.
- Error checking.
- Comparison with real measurements.
