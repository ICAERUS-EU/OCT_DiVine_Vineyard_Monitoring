
<div align="center">
  <p>
    <a href="https://icaerus.eu" target="_blank">
      <img width="50%" src="https://raw.githubusercontent.com/ICAERUS-EU/.github/refs/heads/main/profile/ICAERUS_transparent.png"></a>
    <h3 align="center">OCT_DiVine_Vineyard_Monitoring</h3>
    
   <p align="center">
    The project goal is Discovering Invisible VIne Nutrition Elements (DiVine) by developing detailed digital vineyard maps that can distinctly identify areas likely affected by disease from those suffering from nutritional deficiencies. The repository contains several scripts for 
     1. Reading a (vineyard) map (TIF, PNG, JPG formats) and providing a user-led tool for ROI annotation and extraction. 
     2. Converting .json files, containing disease detection results, into .jpg images suitable for visualisation. It is specifically designed for images captured  by the DJI Mavic 3M drone.
     3. Extracting several (default: 4) sampling regions from the vegetation index map. 
     4. Performing semi-automatic vine position extraction by using several input parameters: distance between rows and distance between lines.
     5. Calculating 4 vegetation indices ('NDVI', 'MSAVI2', 'NDRE', 'NLI') and displaying the results.
    <br/>
    <br/>
    <a href="https://github.com/icaerus-eu/repo-title/wiki"><strong>Explore the wiki »</strong></a>
    <br/>
    <br/>
    <a href="https://github.com/icaerus-eu/repo-title/issues">Report Bug</a>
    -
    <a href="https://github.com/icaerus-eu/repo-title/issues">Request Feature</a>
  </p>
</p>
</div>

![Downloads](https://img.shields.io/github/downloads/icaerus-eu/repo-title/total) ![Contributors](https://img.shields.io/github/contributors/icaerus-eu/repo-title?color=dark-green) ![Forks](https://img.shields.io/github/forks/icaerus-eu/repo-titlee?style=social) ![Stargazers](https://img.shields.io/github/stars/icaerus-eu/repo-title?style=social) ![Issues](https://img.shields.io/github/issues/icaerus-eu/repo-title) ![License](https://img.shields.io/github/license/icaerus-eu/repo-title) 

## Table Of Contents
- [Summary](#summary)
- [Structure](#structure)
- [Methods](#methods)
- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [Authors](#authors)
- [Requirements](#requirements)
- [Acknowledgments](#acknowledgments)


## Summary
The project's main goal is the development of detailed digital vineyard maps that can distinctly identify areas likely affected by disease from those suffering from nutritional deficiencies. The starting point is the calculation of vegetation indices suitable for vineyards in order to identify areas under stress; from there, we
1) first apply a disease detection model to identify vines attacked by a disease,
2) extract areas under stress to perform in-field testing to detect nutrition deficiency,
3) combine results.

## Structure
The repository folders are structured as follows:
1. data: some examples of a vineyard orthomosaics
2. methods: methods necessary for the final creation of the detailed maps
3. auxiliary files

## Methods
1. Reading a (vineyard) map (TIF, PNG, JPG formats) and providing a user-led tool for ROI annotation and extraction. 
2. Converting .json files, containing disease detection results, into .jpg images suitable for visualisation. It is specifically designed for images captured  by the DJI Mavic 3M drone.
3. Extracting several (default: 4) sampling regions from the vegetation index map. 
4. Performing semi-automatic vine position extraction by using several input parameters: distance between rows and distance between lines.
5. Calculating 4 vegetation indices ('NDVI', 'MSAVI2', 'NDRE', 'NLI') and displaying the results.

## Installation
Install all dependencies using `pipenv`

## Usage
1. ROI Extraction: 
Clone the repository or copy the script files;
Place your image/map in the working directory or change the image path in the code;
Run the script;
When prompted, select ROI by clicking on the scaled image;
Wait for the clustering and segmentation results.

2. JSON to JPG: 
Clone the repository or copy the script files;
Change the file path toward your .json and .jpg (or .tif) files;
Define labels as in your .json files; define label colours; 
Adjust the file name: for json_path in glob(os.path.join(json_dir, "*_D.JSON"));
Run the script;
Wait for the results.

3. Sampling regions extraction:
Clone the repository or copy the script files;
Place your image in the working directory or change the file path;
Define input parameters directly in the code: scaling factor (default: 0.125), number of Kmeans clusters (default: k = 4);
Run the script;
When prompted, select ROI by clicking corners on the scaled image;
Wait for the results (after each visualization, close the window in order for the code to continue).

4. Semi-automatic vines extraction:
Clone the repository or copy the script files;
Place your image in the working directory or change the file path;
Define input parameters directly in the code: distance between rows (in pixels), distance between lines (in pixels), scaling factor (default: 0.25);
Run the script;
When prompted, select ROI by clicking 4 corners on the scaled image;
Wait for the results.

5. Vegetation indices calculation:
Clone the repository or copy the script files;
Place your spectral bands in the working directory or change the file paths;
Run the script.

## Features

1. ROI Extraction:
Load a map of a vineyard (it can be any other field);
Resize a map for displaying (in some cases, GeoTIF maps can be too large for displaying);
Open a window for manual polygon selection (the user can select a polygon of any shape by drawing points);
Crop a polygon/ROI and create a mask that can be later used for ROI extraction.

2. JSON to JPG:
Load .json files together with new (clean) images that will be used for visualisation;
Define which labels should be extracted (in the example, 3 labels are defined: "eska", "meska", "ostalo");
Find matching images and transfer the labels to .jpg files for easier visualisation;
Transfer camera details.

3. Sampling regions extraction:
Load a (vineyard) map - vegetation index - for displaying;
Resize the map for displaying and ROI selection;
Allows interactive ROI selection: the user chooses points that mark an ROI polygon;
Performs K-means clustering only inside the ROI (default: k = 4);
Visualise the result of K-means;
Visualise the sampling regions.

4. Semi-automatic vines extraction:
Load and resize a (vineyard) map for displaying;
Allows interactive ROI selection: user marks 4 corners of a vineyard;
Generates a vine grid from 4 corners;
Calculate the number of vines and generate a grid.

5. Vegetation indices calculation:
Load separately spectral bands (Red, RedEdge, and NIR);
Calculate indices;
Display the results (4 indices in one figure); The user can change a colormap directly in the code.

## Authors
Marina Ljubenovic, CTO Veles Sense,
email: marina@velessense.com

## Requirements
- Python 3.8+
- Dependencies:
  - `numpy`
  - `opencv-python`
  - `scikit-learn`
  - `matplotlib`
  - `rasterio`
  - `scikit-image`

## Acknowledgements
This project is funded by the European Union, grant ID 101060643.

<img src="https://rea.ec.europa.eu/sites/default/files/styles/oe_theme_medium_no_crop/public/2021-04/EN-Funded%20by%20the%20EU-POS.jpg" alt="https://cordis.europa.eu/project/id/101060643" width="200"/>

