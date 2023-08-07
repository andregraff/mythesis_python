1. Project Description

This repository aims to recreate a part of the energy simulation work conducted using EnergyPlus for my Master's thesis ([link here](https://etd.adm.unipi.it/t/etd-01262022-164701/)) with a newer version of En+ (from v8.9 --> 22.2). It utilizes a Python script to expedite, automate, and reduce errors in the process.
You must have EnergyPlus v22.2 installed in your machine.


2. Table of contents
```
   This repo contains:

- /#enplus_models        # with all the '.idf' files for the simulation in the city of Bolzano and Palermo
- /csv_outputs           # all the csv dataframes of the new results
- /images_outputs        # all the images
- Energy+.idd            # the input data dictionary of EnergyPlus v22.2
- *.epw files            # the weather files for the simulation in EnergyPlus
- my_thesis_with_.py     # the main file
- requirements.txt       # list of all libraries for the env
- OLD_total.xlsx         # with the KPIs of the thesis work to be compared
```
3. How it Works

The main function of the Python file has three input arguments: run_files=None, add_output=None, collect_kpi=None. If you add "run_files", the simulation of all models within the #allmodels folder will be executed. If you add "add_output", you can include an output variable at a specific position in the IDF file. If you add "collect_kpi", CSV files will be created inside the 'csv_outputs' folder.

The Python script performs the following actions:
```
- Initialization: The script starts with some import statements and variable declarations. It imports required libraries like matplotlib, os, pandas, re, imgkit, and classes like IDF from the eppy.modeleditor module. It also sets the version number (enplus_vers) and defines some base case identifiers.
- Common Functions: This section contains utility functions used in the main script. Some of these functions include searching for files with specific extensions in a directory, generating directories based on combinations of values, renaming files and folders, adding output lines to IDF files, and calculating percentage differences between values.
- Main Function: The main function orchestrates the entire script's execution. It performs the following tasks:
a. Search for IDF files in the root folder.
b. Optionally add output lines to all IDF files to retrieve specific simulation results.
c. Optionally run all IDF files using EnergyPlus with different weather files (Bolzano and Palermo).
d. Search for ESO files (EnergyPlus output) generated by the simulations.
e. Optionally collect key performance indicators (KPIs) such as total cooling and heating loads from ESO files.
f. Compare the KPIs with previous results from an old Excel file and calculate percentage differences and rankings.
g. Generate styled DataFrames and export the results to CSV and HTML files.
h. Export the styled DataFrame as an image (jpg).

```

4. How to Run
```
- Download the repository. You can move the repository anywhere, but avoid changing the names or folders inside it.
- Install the required dependencies.
- Install 'imgkit.
- Unzip the folders.
- Run the Python file. The first time you run the file, set 'run_files=True' to obtain the outputs.
```
5. Results

![Alt Text](images_outputs/styled_df.jpg) 
