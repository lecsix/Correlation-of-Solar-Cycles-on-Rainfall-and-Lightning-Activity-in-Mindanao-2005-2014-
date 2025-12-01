# Correlation-of-Solar-Cycles-on-Rainfall-and-Lightning-Activity-in-Mindanao-2005-2014-
Python code for rainfall–lightning climate analysis over Mindanao (2005–2014), using TRMM/GPM, WWLLN, SOM-based thunderstorm classes, and TRMM–PAGASA validation.

TITLE
CORRELATION OF SOLAR CYCLES ON RAINFALL AND LIGHTNING ACTIVITY IN MINDANAO (2005 -- 2014): A SPATIO -- TEMPORAL ANALYSIS

OVERVIEW
This repository contains the Python code used in the thesis on the correlation between solar activity and the rainfall–lightning climate over Mindanao, Philippines, for 2005–2014.

The scripts

preprocess TRMM/GPM 3-hourly rainfall and WWLLN lightning data on a 0.25° × 0.25° Mindanao grid

aggregate rainfall and lightning into diurnal, Carrington (27-day), seasonal, and Schwabe (yearly) cycles

build rainfall + lightning feature vectors and apply a self-organizing map (SOM) with Ward clustering to define four thunderstorm classes (RLC1–RLC4)

generate intensity maps, average cycle clock maps, and thunderstorm classification maps for each cycle

validate TRMM/GPM rainfall against PAGASA station data for each cycle, including error metrics by station and by thunderstorm class

REPOSITORY STRUCTURE

data_preprocessing/
Scripts to
– read raw TRMM/GPM NetCDF files and WWLLN CSV files
– subset the Mindanao domain
– aggregate daily values and convert them to cycle intensity maps

som_classification/
Scripts to
– construct rainfall–lightning feature vectors per grid cell
– train the SOM
– apply Ward clustering and relabel clusters into RLC1–RLC4
– save class maps for each temporal cycle

mapping_and_figures/
Scripts to
– plot rainfall and lightning intensity maps for each cycle
– draw diurnal and Carrington clock plots
– plot SOM-based thunderstorm classification maps

validation/
Scripts to
– collocate TRMM/GPM grid cells with PAGASA stations
– compute station-level and RLC-aggregated error metrics (bias, MAE, RMSE, relative bias, correlation)
– export tables that correspond to the thesis appendices

notebooks/
Optional Jupyter notebooks that demonstrate the full workflow step by step (from raw data to figures and tables).

docs/
Additional notes on data sources, file naming conventions, and figure settings used in the thesis.

DATA REQUIREMENTS

The repository does not redistribute the original datasets. To reproduce the results, you need to obtain:

– TRMM 3B42RT (and/or GPM successor) 3-hourly rainfall for 2005–2014
– WWLLN lightning stroke data for 2005–2014
– PAGASA 6-hourly station rainfall data for the Mindanao stations used in the thesis
– F10.7 cm solar radio flux (daily)

Place the raw data under a local data/ directory and update the paths in the configuration section of each script (for example RR_DIR, LD_DIR, STATION_FILE).

PYTHON ENVIRONMENT

The analysis was run with Python 3.12.6 and the following main packages:

– numpy
– pandas
– xarray
– matplotlib
– cartopy
– scikit-learn
– minisom

A requirements file is provided in requirements.txt. Create and activate a virtual environment, then install dependencies with

pip install -r requirements.txt

HOW TO RUN

Preprocess and aggregate
Run the scripts in data_preprocessing to
– build daily rainfall and lightning fields
– aggregate them to diurnal, Carrington, seasonal, and yearly cycles
– save cycle intensity maps as NetCDF files

SOM classification
Run the scripts in som_classification to
– read the cycle intensity maps
– build feature vectors
– train the SOM and cluster to K = 4
– save the class label maps (RLC1–RLC4) for each cycle

Mapping and figures
Use the scripts in mapping_and_figures to reproduce the maps and plots shown in the thesis, including
– rainfall and lightning intensity maps
– diurnal and Carrington clock plots
– SOM thunderstorm classification maps

Validation
Run the scripts in validation to
– assign each PAGASA station to an RLC based on the nearest grid cell
– compute station-level and RLC-aggregated metrics
– export CSV tables that match the thesis appendices

CODE–THESIS LINK

The code corresponds to the analyses described in the Methodology and Appendix sections of the thesis “Correlation of Solar Cycles on Rainfall and Lightning Activity in Mindanao (2005–2014): A Spatio-Temporal Analysis.”
Each major script includes comments that point to the relevant figures and tables in the manuscript.

LICENSE

Specify your chosen open-source license here (for example MIT License) and include the license file in the repository.

CITATION

If you use this code, please cite the thesis and this repository using the recommended citation in the docs/ or README file.
