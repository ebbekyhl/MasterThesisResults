# MasterThesisResults
This repository consists of the modelled inflow time series obtained with ATLITE, and historical inflow acquired from various sources. 
The main script trains the modelled inflow at the beginning of century (BOC) using historical inflow to obtain a month and country dependent 
retain factor which is subsequently applied to calibrate modelled inflow at the end of century (EOC). 
The following Python modules were applied to run the script:
> numpy 1.19.1, matplotlib 3.1.0, pandas 1.0.3, scipy 1.5.2

The full procedure of achieving the time series is described in the following. Step 1, 2, and 3 have already been performed, but can be repeated if new and improved GCM or RCM emerge.

## 1: Download climate model data from CORDEX
https://esgf-data.dkrz.de/search/cordex-dkrz/ 

## 2: Convert EURO-CORDEX .nc files into ATLITE cutouts
Run the script __Cordex_to_Atlite_converter.py__ by first defining the variables:
- years_list: List of 5 years intervals
- dr_model_list: General circulation model (called driving model in CORDEX terms)
- rcm_list: Regional climate model
It creates monthly .nc files which will later be used in conversion of runoff into inflow time series (Step 3).
(This script was run on the cluster. It requires extensive disc space.)

## 3: Convert gridded runoff into hourly inflow time series with ATLITE
Run the script __create_modelled_inflow_csv_BIGRUN.py__ (again, define years, driving model, and rcm).
The output is .csv files of 5 years intervals on a country-level.

## 4: Calibrate modelled inflow and map the results
Run the script __Climate_change_impact_hydro_Map_Results.py__ which trains and calibrate the modelled data, and subsequently illustrates the impact by plotting 
a map that indicates the change in the annual inflow and the change of the seasonal shape. Furthermore, a figure depicts the interannual variability with the probability 
density functions of the annual inflow within the two eras, BOC and EOC.
