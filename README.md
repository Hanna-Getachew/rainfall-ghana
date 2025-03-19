# rainfall-ghana
Daily rainfall data for 2023 and 2024 in Ghana, extracted from Google Earth Engine (CHIRPS dataset).
# Rainfall Data for Ghana (2023-2024)

## Overview
This repository contains daily rainfall data for all of Ghana for the years 2023 and 2024. The data is extracted using Google Earth Engine (GEE) from the CHIRPS Daily Precipitation dataset. This repository also includes scripts and documentation to process, analyze, and visualize the data.

## Data Source
- **Dataset:** CHIRPS Daily Precipitation ([UCSB-CHG/CHIRPS/DAILY](https://developers.google.com/earth-engine/datasets/catalog/UCSB-CHG_CHIRPS_DAILY))
- **Resolution:** ~5.5 km grid
- **Time Period:** January 1, 2023 – December 31, 2024
- **Region:** Ghana (national coverage)

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

rainfall_data <- read_csv("https://raw.githubusercontent.com/yourusername/Rainfall_Ghana/main/Rainfall_Ghana_All_2023_2024.csv")
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

## Uploading Data to GitHub
To upload the dataset to GitHub:
1. Move to your local repository directory.
```bash
cd /path/to/your/repository
```
2. Copy the CSV file into the repository folder.
```bash
cp /path/to/Rainfall_Ghana_All_2023_2024.csv .
```
3. Add the file to Git.
```bash
git add Rainfall_Ghana_All_2023_2024.csv
```
4. Commit the changes.
```bash
git commit -m "Added rainfall dataset for Ghana (2023-2024)"
```
5. Push to GitHub.
```bash
git push origin main
```

## Future Work
- Integrate temperature data for climate impact analysis.
- Calculate additional drought indices such as the Standardized Precipitation Index (SPI).
- Compare rainfall patterns with agricultural productivity data.

## Contact
For questions or contributions, please open an issue or submit a pull request.

Author: [Your Name]  
Email: your.email@example.com

