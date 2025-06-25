# Dataset title

## Table of Contents

- [1. GENERAL INFORMATION](#1-general-information)
- [2. METHODOLOGICAL INFORMATION](#2-methodological-information)
  - [2.1 Research questions, methods and envisioned uses](#21-research-questions-methods-and-envisioned-uses)
  - [2.2 Methods for processing the data](#22-methods-for-processing-the-data)
  - [2.3 Instrument- or software-specific information](#23-instrument--or-software-specific-information)
- [3. FILE OVERVIEW](#3-file-overview)
  - [3.1 File List](#31-file-list)
  - [3.2 Relationship between files](#32-relationship-between-files)
  - [3.3 File formats and naming conventions](#33-file-formats-and-naming-conventions)
- [4. DATA-SPECIFIC INFORMATION](#4-data-specific-information)
  - [4.1 Data Category A](#41-data-category-a)
  - [4.2 Data Category B](#42-data-category-b)
  - [4.3 Data Category C](#43-data-category-c)
  - [4.4 Data Category D](#44-data-category-d)
- [5. SHARING/ACCESS INFORMATION](#5-sharingaccess-information)
  - [5.1 Licenses/restrictions placed on the data](#51-licensesrestrictions-placed-on-the-data)
  - [5.2 Links to other resources](#52-links-to-other-resources)
  - [5.3 Recommended citation for this dataset](#57-recommended-citation-for-this-dataset)


# 1. GENERAL INFORMATION

## 1.1 Title of Dataset
ReBioClim Dresden: Spatial Analysis Dataset for Urban Stream Restoration

## 1.2 Dataset description
This dataset contains quantitative spatial data on biodiversity, quality of life, and climate adaptation metrics for Dresden, Germany, organised in a 500x500m grid system. The data supports urban stream restoration planning by providing a multi-criteria analysis framework to identify priority areas that would benefit most from restoration interventions. The dataset was developed as part of the ReBioClim project, an Interreg Central Europe initiative focused on enhancing biodiversity and climate resilience through urban stream restoration. Additional details about the ReBioClim project can be accessed [here](https://www.interreg-central.eu/projects/rebioclim/).

## 1.3 Author Information
A. Principal Investigator  
- Name: Daan Schlosser
- Institution: Delft University of Technology
- Address: Julianalaan 134, 2628 BZ Delft
- Email: d.h.schlosser@student.tudelft.nl

B. Associate investigator
- Name: Joost Bastiaansen
- Institution: Delft University of Technology, 
- Address: Julianalaan 134, 2628 BZ Delft
- Email: j.w.a.bastiaansen@student.tudelft.nl

C. Associate investigator
- Name: Aparnaa Chandrasekaran
- Institution: Delft University of Technology
- Address: Julianalaan 134, 2628 BZ Delft
- Email: a.chandrasekaran-1@student.tudelft.nl

D. Associate investigator
- Name: Teun van Dijk
- Institution: Delft University of Technology
- Address: Julianalaan 134, 2628 BZ Delft
- Email: t.vandijk-4@student.tudelft.nl

## 1.4 Dates of data collection
- Primary data processing: 2025-05-21 to 2025-06-17
- NDVI satellite data: May 2023 to May 2024 (Copernicus)
- Municipal data sources: Various dates (latest available releases from Dresden municipality as of May 2025)

## 1.5 Geographic location of data collection
Dresden, Germany

## 1.6 Keywords
urban stream restoration, biodiversity, climate adaptation, quality of life, spatial analysis, urban planning, Dresden, multi-criteria analysis, GIS

## 1.7 Language
English

## 1.8 Information about funding sources that supported the collection of the data
N/A

# 2. METHODOLOGICAL INFORMATION
## 2.1 Research questions, methods and envisioned uses
This dataset was developed to support spatial decision-making for urban stream restoration projects through multi-criteria analysis of environmental and social factors.

### 2.1.1 Research question: What areas of Dresden would stand to gain the most from urban stream restoration projects?
- GIS-based spatial analysis of municipal datasets (quantitative)
- Satellite-derived vegetation indices (quantitative)
- Multi-criteria evaluation framework (quantitative)

### 2.1.2 Envisioned uses of the dataset
- Urban planning and stream restoration prioritization
- Environmental impact assessment and monitoring
- Academic research on urban sustainability and green infrastructure
- Municipal decision support for environmental interventions
- Comparative studies of urban environmental metrics

## 2.2 Methods for processing the data
- Regridding of municipal datasets to standardized 500x500m grid system using area-weighted averaging
- NDVI calculation from Copernicus satellite imagery (May 2023 - May 2024)
- Normalization of all metrics to 0-1 scale where 1 represents optimal conditions
- Spatial analysis using buffer operations and proximity calculations
- Integration of multiple data sources through weighted overlay analysis
- K-means clustering analysis in R using BIO_Weighted, CLI_Weighted, and QOL_Weighted scores for typology calculations

## 2.3 Instrument- or software-specific information
- QGIS used for spatial analysis and data processing
- R software used for typology analysis and k-means clustering
- Copernicus satellite data for NDVI calculations
- Dresden municipality WFS endpoint as primary data source

# 3. FILE OVERVIEW
Are there multiple versions of the dataset? No

## 3.1 File List

### 3.1.1 Primary dataset
- "Grid_BIO_CLI_QOL.gpkg": Geopackage containing 500x500m grid (698 cells) with all biodiversity, quality of life, and climate adaptation metrics

### 3.1.2 Documentation
- "README.md": This documentation file
- Links to Dresden municipality WFS endpoints (provided in section 5.2)

## 3.2 Relationship between files:
The geopackage contains a single spatial layer with all metrics as attributes. No foreign key relationships exist as all data is contained within one table.

## 3.3 File formats and naming conventions
### 3.3.1 File formats
- .gpkg - Geopackage format containing spatial grid data with attribute table

### 3.3.2 Naming conventions
- Files named in lower case, spaces replaced with dashes (dash-case)
- Variable names use descriptive prefixes (BIO_, QOL_, CLI_) followed by descriptive names

# 4. DATA-SPECIFIC INFORMATION

- Missing data code: NA
- Not Applicable: N/A
- All metrics normalized to 0-1 scale where 1 = best performing/optimal conditions, 0 = worst performing/needs immediate attention

## 4.1 Biodiversity Metrics

### 4.1.1 Variables in Grid_BIO_CLI_QOL.gpkg
Number of biodiversity variables: 5

**id**
- Full name: Grid Cell Identifier
- Description: Unique identifier for each 500x500m grid cell
- Type of variable: Integer
- Unit of measurement: Sequential ID number

**BIO_PM10**
- Full name: PM10 Air Pollution
- Description: PM10 (airborne particulate matter ≤10 micrometers) concentration levels
- Type of variable: Continuous (0-1 normalized)
- Unit of measurement: Normalized from µg/m³ (original range: 0-45)
- Calculation: Area-weighted regridding of municipal pollution data, rescaled where 0 = >45 µg/m³, 1 = 0 µg/m³

**BIO_NO2**
- Full name: NO2 Air Pollution  
- Description: Nitrogen dioxide concentration levels
- Type of variable: Continuous (0-1 normalized)
- Unit of measurement: Normalized from µg/m³ (original range: 0-40)
- Calculation: Area-weighted regridding of municipal pollution data, rescaled where 0 = >40 µg/m³, 1 = 0 µg/m³

**BIO_GreenBluePercentage**
- Full name: Green and Blue Space Coverage
- Description: Percentage of grid cell classified as green or blue space (net area)
- Type of variable: Continuous (0-1)
- Unit of measurement: Proportion (0 = 0% green/blue, 1 = 100% green/blue)
- Calculation: Area-weighted calculation from municipal land use classification

**BIO_LandscapeQuality**
- Full name: Landscape Quality Assessment
- Description: Municipal assessment of landscape quality and value
- Type of variable: Ordinal (0-1 normalized)
- Unit of measurement: Normalized quality scale
- Calculation: Municipal classifications converted to numeric scale (Very low=0.0, Low=0.25, Medium=0.5, High=0.75, Very high/Unique=1.0)

**BIO_NDVI**
- Full name: Normalized Difference Vegetation Index
- Description: Annual average NDVI from satellite imagery
- Type of variable: Continuous (0-1 normalized)
- Unit of measurement: Normalized NDVI
- Calculation: Mean NDVI from Copernicus satellite (May 2023-May 2024), transformed from (-1,1) to (0,1) scale using (x+1)/2

## 4.2 Quality of Life Metrics

### 4.2.1 Variables in Grid_BIO_CLI_QOL.gpkg
Number of quality of life variables: 6

**QOL_RecreationalSuitability**
- Full name: Recreational Suitability Assessment
- Description: Municipal assessment of area suitability for recreation
- Type of variable: Ordinal (0-1 normalized)
- Unit of measurement: Normalized suitability scale
- Calculation: Municipal classifications converted (Not suitable=0.0, Low value=0.25, Somewhat suitable=0.5, Regionally important=0.75, Highly suitable=1.0)

**QOL_VicinityToUrbanGreenSpaces**
- Full name: Access to Urban Green Spaces
- Description: Accessibility measure to urban green spaces adjusted for address density and green space area
- Type of variable: Continuous (0-1 normalized)
- Unit of measurement: Normalized accessibility index
- Calculation: Space syntax analysis normalized by maximum value, then log-transformed

**QOL_VicinityToStreams**
- Full name: Proximity to Water Bodies
- Description: Average distance from addresses to streams within 500m buffer
- Type of variable: Continuous (0-1 normalized) 
- Unit of measurement: Normalized distance measure (0 = closest, 1 = furthest)
- Calculation: Average address-to-stream distance per grid, normalized and log-transformed

**QOL_Facilities**
- Full name: Recreation Facilities Count
- Description: Number of playground and seating facilities per grid cell
- Type of variable: Continuous (0-1 normalized)
- Unit of measurement: Normalized facility count
- Calculation: Sum of facilities per grid, normalized by maximum count, then log-transformed

**QOL_LocalIntegration**
- Full name: Local Integration Index
- Description: Average local integration measure per grid tile
- Type of variable: Continuous
- Unit of measurement: Integration index value

**QOL_CoveredStreamDistance**
- Full name: Covered Stream Length
- Description: Total length of covered stream length per tile
- Type of variable: Continuous (0-1 normalized)
- Unit of measurement: Distance (meters), Normalized distance (0 = none, 1 = longest)
- Calculation: Stream length normalized using a piecewise linear scale (0 for ≤140 m, 1 for ≥2500 m), rounded to 3 decimals

## 4.3 Climate Adaptation Metrics

### 4.3.1 Variables in Grid_BIO_CLI_QOL.gpkg
Number of climate adaptation variables: 5

**CLI_Infiltration**
- Full name: Soil Infiltration Capability
- Description: Municipal classification of soil infiltration capacity
- Type of variable: Ordinal (0-1 normalized)
- Unit of measurement: Normalized infiltration capacity
- Calculation: Municipal classifications rescaled using (value-1)/4 where 1 = optimal infiltration

**CLI_SealingClass**
- Full name: Surface Sealing Classification
- Description: Degree of surface sealing requiring intervention
- Type of variable: Ordinal (0-1 normalized)
- Unit of measurement: Normalized sealing degree (0 = most sealed, 1 = least sealed)
- Calculation: VSG classifications normalized (VSG <10% excluded, 10-20%=1.0, 20-40%=0.75, 40-60%=0.5, 60-80%=0.25, 80-100%=0.0)

**CLI_SoilStorage**
- Full name: Soil Water Storage Capacity
- Description: Municipal ranking of soil water storage capabilities
- Type of variable: Ordinal (0-1 normalized)
- Unit of measurement: Normalized storage capacity
- Calculation: Classifications rescaled using (value-1)/4 where 1 = highest storage capacity

**CLI_UrbanHeatIsland**
- Full name: Urban Heat Island Effect
- Description: Urban heat island index indicating temperature elevation
- Type of variable: Continuous (0-1 normalized)
- Unit of measurement: Normalized UHI index
- Calculation: UHI values <7 excluded, remaining normalized 0-1 where 0 = highest heat effect (28-35 index), 1 = lowest heat effect

**CLI_UrbanTrees**
- Full name: Urban Tree Density Near Streams
- Description: Count of trees within 10m buffer of streams
- Type of variable: Ordinal (0-1)
- Unit of measurement: Normalized tree count classes
- Calculation: Tree counts classified (0-25=0.0, 26-50=0.25, 51-75=0.5, 76-100=0.75, >100=1.0; forest areas assigned 0.5)

## 4.4 Weighted Scores and Typology Analysis

### 4.4.1 Additional variables in Grid_BIO_CLI_QOL.gpkg
Number of derived variables: 4

**BIO_Weighted**
- Full name: Biodiversity Composite Score
- Description: Weighted composite score of all biodiversity metrics
- Type of variable: Continuous (0-1)
- Unit of measurement: Normalized composite score
- Calculation: Weighted average of BIO_PM10, BIO_NO2, BIO_GreenBluePercentage, BIO_LandscapeQuality, and BIO_NDVI using theme-specific weights

**QOL_Weighted**
- Full name: Quality of Life Composite Score
- Description: Weighted composite score of all quality of life metrics
- Type of variable: Continuous (0-1)
- Unit of measurement: Normalized composite score
- Calculation: Weighted average of all QOL variables using theme-specific weights

**CLI_Weighted**
- Full name: Climate Adaptation Composite Score
- Description: Weighted composite score of all climate adaptation metrics
- Type of variable: Continuous (0-1)
- Unit of measurement: Normalized composite score
- Calculation: Weighted average of all CLI variables using theme-specific weights

**Overall_Weighted**
- Full name: Overall Composite Score
- Description: Overall weighted composite score across all three themes
- Type of variable: Continuous (0-1)
- Unit of measurement: Normalized composite score
- Calculation: Weighted combination of BIO_Weighted, QOL_Weighted, and CLI_Weighted scores

Total number of variables: 21 (1 ID + 5 biodiversity + 6 quality of life + 5 climate adaptation + 4 composite scores)
Total number of grid cells: 698

# 5. SHARING/ACCESS INFORMATION
## 5.1 Licenses/restrictions placed on the data:
This dataset is licensed under Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0). You are free to share and adapt the material for any purpose, even commercially, under the following terms: you must give appropriate credit, provide a link to the license, and indicate if changes were made. If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.

## 5.2 Links to other resources:

### 5.2.1 Links to publications that cite or use the data:
To be updated upon publication

### 5.2.2 Links to other publicly accessible locations of the data: 
To be determined

### 5.2.3 Links/relationships to ancillary data sets: 
- Dresden Municipality WFS Endpoints (various environmental and urban planning datasets)
- Copernicus Sentinel satellite imagery (NDVI data source)
- ReBioClim project data repository: https://www.interreg-central.eu/projects/rebioclim/

### 5.2.4 Links to publicly accessible scripts for analysis of the dataset:
- ([GitHub GroupE repository](https://github.com/sdgis-edu-tud/report-asa2025-groupe))

### 5.2.5 Was data derived from another source?
Yes - Primary sources include Dresden municipality open data via WFS endpoints and Copernicus satellite imagery. All processing and analysis conducted by the research team.

## 5.3 Recommended citation for this dataset:
Schlosser, D., Bastiaansen, J., Chandrasekaran, A., & van Dijk, T. (2025). ReBioClim Dresden: Spatial Analysis Dataset for Urban Stream Restoration Prioritization. Delft University of Technology. [DOI to be assigned]

---

This README.md file template was generated on 2022-04-19 by Claudiu Forgaci and Adele Therias according to the 4TU.ResearchData [Guidelines for creating a README file](https://data.4tu.nl/info/en/use/publish-cite/upload-your-data-in-our-data-repository) and the Cornell University template [Guide to writing "readme" style metadata](https://cornell.app.box.com/v/ReadmeTemplate) and is licensed under CC BY 4.0
