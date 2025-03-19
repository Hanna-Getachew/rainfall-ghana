# rainfall-ghana
Daily rainfall data for 2023 and 2024 in Ghana, extracted from Google Earth Engine (CHIRPS dataset).

# Rainfall Data for Ghana (2023-2024)

## Overview
This repository contains daily rainfall data for all of Ghana for the years 2023 and 2024. The data is extracted using Google Earth Engine (GEE) from the CHIRPS Daily Precipitation dataset. This repository also includes scripts and documentation to process, analyze, and visualize the data.

Additionally, we are obtaining rainfall and temperature data for **survey clusters in northern Ghana**. These clusters correspond to **200 villages and 3,000 households**, where data collection occurred in **late 2023**, and a second wave is taking place shortly. During the 2024 growing season, **prolonged dry spells led to significant harvest losses**, making it necessary to proxy drought severity using various indices.

## Data Source
- **Dataset:** CHIRPS Daily Precipitation ([UCSB-CHG/CHIRPS/DAILY](https://developers.google.com/earth-engine/datasets/catalog/UCSB-CHG_CHIRPS_DAILY))
- **Resolution:** ~5.5 km grid
- **Time Period:** January 1, 2023 – December 31, 2024
- **Region:** Ghana (national coverage)

## Drought Indices
The study focuses on **measuring drought severity in 2024** using multiple indices, including:
- **Consecutive Dry Days (CDD)** – Number of consecutive days with precipitation below a threshold.
- **Rainfall Anomaly Index (RAI)** – Measures deviations from normal rainfall.
- **Standardized Precipitation Index (SPI)** – Quantifies rainfall deficits based on long-term distribution.
- **Standardized Precipitation Evapotranspiration Index (SPEI)** – Accounts for both precipitation and potential evapotranspiration.

## Repository Structure
```
📁 Rainfall_Ghana  
│── 📄 README.md                 # Project documentation  
│── 📄 Rainfall_Ghana_All_2023_2024.csv  # Processed rainfall data  
│── 📄 rainfall_extraction.js    # Google Earth Engine script  
│── 📄 rainfall_analysis.R       # R script for processing & visualization  
│── 📄 rainfall_workflow.Rmd     # R Markdown explaining the full process  
```

## Data Description
The dataset contains the following columns:
| Column        | Description |
|--------------|------------|
| `date`       | Date (YYYY-MM-DD) |
| `rainfall`   | Mean daily precipitation (mm) |

## Extracting Data with Google Earth Engine
The `rainfall_extraction.js` script extracts rainfall data for Ghana using the CHIRPS dataset in Google Earth Engine. The script calculates the mean daily precipitation over the country and exports the data as a CSV.

To run the script:
1. Open Google Earth Engine Code Editor ([code.earthengine.google.com](https://code.earthengine.google.com/)).
2. Copy and paste the `rainfall_extraction.js` script.
3. Run the script and export the CSV file to Google Drive.

## Processing Data in R
Once the data is extracted, it is processed in R using `rainfall_analysis.R`. This script:
- Reads the extracted CSV file.
- Cleans and formats the data.
- Computes drought indices such as consecutive dry days (CDD).
- Generates rainfall trend visualizations.

### Load Data in R
```r
library(readr)

rainfall_data <- read_csv("https://raw.githubusercontent.com/hannagetachew/Rainfall_Ghana/main/Rainfall_Ghana_All_2023_2024.csv")
head(rainfall_data)
```

### Example Visualization
```r
library(ggplot2)
library(dplyr)

rainfall_data %>%
  ggplot(aes(x = as.Date(date), y = rainfall)) +
  geom_line(color = "blue") +
  labs(title = "Daily Rainfall in Ghana (2023-2024)", x = "Date", y = "Rainfall (mm)")
```

## Documentation with R Markdown
The `rainfall_workflow.Rmd` file provides a structured explanation of the entire workflow, from data extraction in Google Earth Engine to analysis in R. It includes:
- A step-by-step guide to running the scripts.
- Explanations of the methods used for data processing and analysis.
- Code snippets and outputs to illustrate key steps.

## Future Work
- Integrate temperature data for climate impact analysis.
- Calculate additional drought indices such as the **Rainfall Anomaly Index (RAI)** and **Standardized Precipitation Evapotranspiration Index (SPEI)**.
- Compare rainfall patterns with agricultural productivity data.

## Contact
For questions or contributions, please open an issue or submit a pull request.

Author: Hanna  
Email: hfgedu@gmail.com

