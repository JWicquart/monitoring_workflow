# **A workflow to integrate ecological monitoring data from multiples sources**



**This repository contains the two case studies presented in the article**:

Wicquart, J., Planes, S. (2020). A workflow to integrate ecological monitoring data from multiples sources. _Methods in Ecology and Evolution_, in prep.

**How to download the code?**

On the project main page on GitHub, click on the green button `clone or download` and then click on `Download ZIP`

**How to report bugs or issues?**

Please report any bugs or issues [HERE](https://github.com/JWicquart/monitoring_workflow/issues).


## 1. Path 3.A - Taxonomical re-categorisation



### 1.1 Context



### 1.2 Project organization

path_3b
├── data
│   ├── 01_raw
│   │   ├── data_contributor_1
│   │   ├── data_contributor_2
│   │   ├── data_contributor_3
│   │   ├── data_contributor_4
│   │   └── data_contributor_5
│   └── 02_reformatted
└── R


### 1.3 Datasets description




### 1.4 Variables selected



The **Table 1** describes the selected variables for the final benthic dataset. The variables 1 to 11 are spatial variables; the variables 12 and 13, are temporal variables; the variables 14 and 15, are methodological variables; the variables 16 to 20 are taxonomical variables; and the variable 21 is the metric variable.



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



 

## 2. Path 3.B - Taxonomical verification



### 2.1 Context



### 2.2 Project organization

path_3b
├── data
│   ├── 01_raw
│   │   ├── data_contributor_1
│   │   ├── data_contributor_2
│   │   ├── data_contributor_3
│   │   ├── data_contributor_4
│   │   └── data_contributor_5
│   └── 02_reformatted
└── R

### 2.3 Datasets description




### 2.4 Variables selected



The **Table 3** describes the selected variables for the final fish dataset. The variables 1 to 11 are spatial variables; the variables 12 and 13, are temporal variables; the variables 14 and 15, are methodological variables; the variables 16 to 18 are taxonomical variables; and the variables 19 and 20 are the metric variables.



|      | Variable    | Type    | Unit          | Description                              |
| ---- | ----------- | ------- | ------------- | ---------------------------------------- |
| 1    | DatasetID   | Factor  |               | Dataset ID                               |
| 2    | Area        | Factor  |               | Biogeographic area                       |
| 3    | Country     | Factor  |               | Country                                  |
| 4    | Archipelago | Factor  |               | Archipelago                              |
| 5    | Location    | Factor  |               | Location or island within the country    |
| 6    | Site        | Factor  |               | Site within the location                 |
| 7    | Replicate   | Integer |               | Replicate ID                             |
| 8    | Zone        | Factor  |               | Reef zone                                |
| 9    | Latitude    | Numeric |               | Latitude of the site (*decimal format*)  |
| 10   | Longitude   | Numeric |               | Longitude of the site (*decimal format*) |
| 11   | Depth       | Numeric | m             | Mean depth                               |
| 12   | Year        | Integer |               | Year                                     |
| 13   | Date        | Date    |               | Date (*YYYY-MM-DD*)                      |
| 14   | Method      | Factor  |               | Description of the method used           |
| 15   | Observer    | Factor  |               | Name of the diver                        |
| 16   | Family      | Factor  |               | Family                                   |
| 17   | Genus       | Factor  |               | Genus                                    |
| 18   | Species     | Factor  |               | Species                                  |
| 19   | Density     | Numeric | n ind. 100 m2 | Number of individuals                    |
| 20   | Size        | Numeric | cm            | Size of individuals                      |



**Table 3.** Variables selected for the fish dataset. The factor levels of the variable `Size_type` are *Total length*, *Fork length* and *Standard length*.