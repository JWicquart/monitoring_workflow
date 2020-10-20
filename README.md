# **A workflow to integrate ecological monitoring data from multiples sources**


This repository is associated with the article "Wicquart, J., Planes, S. (2020). A workflow to integrate ecological monitoring data from multiples sources. *Methods in Ecology and Evolution*, in prep.". The goal of this repository is to provide data and code illustrating the workflow presented in the article, through two case study.

## 1. How to download this project?

On the project main page on GitHub, click on the green button `Code` and then click on `Download ZIP`

## 2. Path 3.A - Taxonomical re-categorisation


### 2.1 Context

The first case study correspond to the path 3A of the workflow and illustrate the integration of data from monitoring of benthic communities (sessile organisms) in coral reefs. Because the taxonomic identification is difficult, broad categories are often used (*e.g.* algae, hard living coral) in most of monitoring programs. Thus, during the data integration, a taxonomical re-categorisation must be done to insure the use a common categories across the different datasets integrated.

### 2.2 Project organization

The folder `path_3a` contains the folders `data` and `R`. The `data` folder regroup all the data files with a numbering corresponding to their level of advancement in the workflow. Hence, the folder `01_raw` contains the different raw data files as received by data contributors, the folder `02_reformatted` contains the individually reformatted datasets, the file *03_synthetic-dataset* correspond to the grouped data with taxonomic assignment done, and the file *04_final-synthetic-dataset* correspond to the final synthetic dataset. This data files and folders numbering is used correspondingly in the `R` folder where three scripts are present. The first one (*step-2_individual-data-reformatting.Rmd*) correspond to the individual data reformatting (step 2 of the workflow) with one or more chunk code by data contributor. The second one (*step-3_data-grouping-tax-assignement.Rmd*) correspond to the data grouping and taxonomic assignement (step 3 of the workflow), and the last one (*step-4_quality-assurance-quality-control.Rmd*) correspond to the quality assurance and quality control (step 4 of the workflow).


### 2.3 Raw datasets description

The `01_raw` folder includes five folders corresponding to the data shared by five different data contributors. Each of them represent a particular situation:

* `data_contributor_1`: One *.xlsx* file containing two sheets, the first one with the main data and the second one with the substrate codes.
* `data_contributor_2`: One *.xlsx* file containing two sheets, the first one with the main data in wide format and the second one with site coordinates.
* `data_contributor_3`: One *.xlsx* file containing three sheets with same columns names corresponding to three different sites. 
* `data_contributor_4`: Three *.csv* files where the two first files contains data for the same site but for two different years, and the third file contains substrate codes.
* `data_contributor_5`: Three *.xlsx* files where the two first files contains data in wide format with different columns names, and the third file contains site coordinates.

### 2.4 Variables selected


The first step of the workflow is to select the variables that will have to be present in the final synthetic dataset. The variables selected for the first case study are described in the **Table 1**. The variables 1 to 11 are spatial variables; the variables 12 and 13, are temporal variables; the variables 14 and 15, are methodological variables; the variables 16 to 20 are taxonomical variables; and the variable 21 is the metric variable.


|      | Variable    | Type    | Unit | Description                              |
| ---- | ----------- | ------- | ---- | ---------------------------------------- |
| 1    | DatasetID   | Factor  |      | Dataset ID                               |
| 2    | Area        | Factor  |      | Biogeographic area                       |
| 3    | Country     | Factor  |      | Country                                  |
| 4    | Archipelago | Factor  |      | Archipelago                              |
| 5    | Location    | Factor  |      | Location or island within the country    |
| 6    | Site        | Factor  |      | Site within the location                 |
| 7    | Replicate   | Integer |      | Replicate ID                             |
| 8    | Zone        | Factor  |      | Reef zone                                |
| 9    | Latitude    | Numeric |      | Latitude of the site (*decimal format*)  |
| 10   | Longitude   | Numeric |      | Longitude of the site (*decimal format*) |
| 11   | Depth       | Numeric | m    | Mean depth                               |
| 12   | Year        | Integer |      | Year                                     |
| 13   | Date        | Date    |      | Date (*YYYY-MM-DD*)                      |
| 14   | Method      | Factor  |      | Description of the method used           |
| 15   | Observer    | Factor  |      | Name of the diver                        |
| 16   | Category    | Factor  |      | See *Table 2*                            |
| 17   | Group       | Factor  |      | See *Table 2*                            |
| 18   | Family      | Factor  |      | Family                                   |
| 19   | Genus       | Factor  |      | Genus                                    |
| 20   | Species     | Factor  |      | Species                                  |
| 21   | Cover       | Numeric | %    | Cover percentage                         |


**Table 1.** Variables selected for the benthic dataset



## 3. Path 3.B - Taxonomical verification


### 3.1 Context

The second case study correspond to the path 3B of the workflow and illustrate the integration of data from monitoring of fish communities (vagile organisms) in coral reefs. Because the monitoring of fish is based on true taxonomical levels (*e.g.* species, genus) instead of broad categories, a taxonomical verification must be assessed during the data integration to avoid misspelling names and include recent update in taxonomy.


### 3.2 Project organization

The folder `path_3b` contains the folders `data` and `R`. The `data` folder regroup all the data files with a numbering corresponding to their level of advancement in the workflow. Hence, the folder `01_raw` contains the different raw data files as received by data contributors, the folder `02_reformatted` contains the individually reformatted datasets, the file *03_synthetic-dataset* correspond to the grouped data with taxonomic assignment done, and the file *04_final-synthetic-dataset* correspond to the final synthetic dataset. This data files and folders numbering is used correspondingly in the `R` folder where three scripts are present. The first one (*step-2_individual-data-reformatting.Rmd*) correspond to the individual data reformatting (step 2 of the workflow) with one or more chunk code by data contributor. The second one (*step-3_data-grouping-tax-assignement.Rmd*) correspond to the data grouping and taxonomic assignement (step 3 of the workflow), and the last one (*step-4_quality-assurance-quality-control.Rmd*) correspond to the quality assurance and quality control (step 4 of the workflow).


### 3.3 Raw datasets description

The `01_raw` folder includes five folders corresponding to the data shared by five different data contributors. Each of them represent a particular situation:

* `data_contributor_1`: One *.xlsx* file containing two sheets, the first one with the main data and the second one with the site coordinates.
* `data_contributor_2`: Two *.csv* files, the first contains the main data in wide format and the second the sites coordinates.
* `data_contributor_3`: One *.xlsx* file containing three sheets, the first contains the main data, the second the site coordinates and the third the species codes.
* `data_contributor_4`: Two files, one in *.xlsx* and one in *.csv*. The *.xlsx* file contains two sheets with same column names, corresponding to two different sites. The *.csv* file contains the site coordinates.
* `data_contributor_5`: Four *.xlsx* files with one sheet, the first three contains the main data with same column names for three different sites, the fourth contains sites coordinates data.


### 3.4 Variables selected

The first step of the workflow is to select the variables that will have to be present in the final synthetic dataset. The variables selected for the second case study are described in the **Table 3**. The variables 1 to 11 are spatial variables; the variables 12 and 13, are temporal variables; the variables 14 and 15, are methodological variables; the variables 16 to 18 are taxonomical variables; and the variables 19 and 20 are the metric variables.


|      | Variable    | Type    | Unit                 | Description                              |
| ---- | ----------- | ------- | -------------------- | ---------------------------------------- |
| 1    | DatasetID   | Factor  |                      | Dataset ID                               |
| 2    | Area        | Factor  |                      | Biogeographic area                       |
| 3    | Country     | Factor  |                      | Country                                  |
| 4    | Archipelago | Factor  |                      | Archipelago                              |
| 5    | Location    | Factor  |                      | Location or island within the country    |
| 6    | Site        | Factor  |                      | Site within the location                 |
| 7    | Replicate   | Integer |                      | Replicate ID                             |
| 8    | Zone        | Factor  |                      | Reef zone                                |
| 9    | Latitude    | Numeric |                      | Latitude of the site (*decimal format*)  |
| 10   | Longitude   | Numeric |                      | Longitude of the site (*decimal format*) |
| 11   | Depth       | Numeric | m                    | Mean depth                               |
| 12   | Year        | Integer |                      | Year                                     |
| 13   | Date        | Date    |                      | Date (*YYYY-MM-DD*)                      |
| 14   | Method      | Factor  |                      | Description of the method used           |
| 15   | Observer    | Factor  |                      | Name of the diver                        |
| 16   | Family      | Factor  |                      | Family                                   |
| 17   | Genus       | Factor  |                      | Genus                                    |
| 18   | Species     | Factor  |                      | Species                                  |
| 19   | Density     | Numeric | n. ind. 100 m-2      | Number of individuals                    |
| 20   | Size        | Numeric | cm                   | Size of individuals                      |


**Table 3.** Variables selected for the fish dataset. The factor levels of the variable `Size_type` are *Total length*, *Fork length* and *Standard length*.

## 4. How to report issues?

Please report any bugs or issues [HERE](https://github.com/JWicquart/monitoring_workflow/issues).

## 5. Reproducibility parameters


