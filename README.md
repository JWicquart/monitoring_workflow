# **A workflow to integrate ecological monitoring data from different sources**

**This repository contains code template illustrating the workflow presented in the article:**

[Wicquart, J., Gudka, M., Obura, D., Logan, M., Staub, F., Souter, D., Planes, S. (2022). A workflow to integrate ecological monitoring data from different sources. *Ecological Informatics*, 68.](https://doi.org/10.1016/j.ecoinf.2021.101543)


## 1. How to download this project?

On the project main page on GitHub, click on the green button `Code` and then click on `Download ZIP`

## 2. Path 3.A - Taxonomic re-categorization


### 2.1 Context

The first case study correspond to the path 3A of the workflow and illustrate the integration of data from monitoring of benthic communities (sessile organisms) in coral reefs. Because the taxonomic identification is difficult, broad categories are often used (*e.g.* algae, hard living coral) in most of monitoring programs. Thus, during the data integration, a taxonomic re-categorization must be done to insure the use of common categories across the different datasets integrated. We highlight that the different datasets were created to illustrate the worklow and they do not correspond to any existing real datasets.


### 2.2 Project organization

The folder `path_3a` contains the folders `data` and `R`. The `data` folder regroup all the data files with a numbering corresponding to their level of advancement in the workflow. Hence, the folder `01_raw` contains the different raw data files as received by data contributors, the folder `02_reformatted` contains the individually reformatted datasets, the file *03_synthetic-dataset* correspond to the grouped data with taxonomic assignment done, and the file *04_final-synthetic-dataset* correspond to the final synthetic dataset. 

Those data files and folders numbering is used correspondingly in the `R` folder where three scripts are present. The first one (*step-2_individual-data-reformatting.Rmd*) correspond to the individual data reformatting (step 2 of the workflow) with one or more chunk code by data contributor. The second one (*step-3_data-grouping-tax-assignment.Rmd*) correspond to the data grouping and taxonomic assignment (step 3 of the workflow), and the last one (*step-4_quality-assurance-quality-control.Rmd*) correspond to the quality assurance and quality control (step 4 of the workflow). 

The *.Rmd* format (rmarkdown) was chosen for the different R scripts because it allows a better segmentation and annotation of the code and process (necessary for the step 2) and the exportation of code and output to an HTML file which may include interactive tables, plots and maps (necessary for steps 3 and 4). The HTML files can be opened with a search engine (*e.g.* Google Chrome) and an internet connection is necessary for the visualization of interactive maps.


### 2.3 Raw datasets description

The `01_raw` folder includes five folders corresponding to the data shared by five different data contributors. Each of them represent a specific case:

* :page_facing_up: `data_contributor_1`: One *.xlsx* file containing two sheets, the first one with the main data and the second one with the substrate codes.
* :page_facing_up: `data_contributor_2`: One *.xlsx* file containing two sheets, the first one with the main data in wide format and the second one with site coordinates.
* :page_facing_up: `data_contributor_3`: One *.xlsx* file containing three sheets with same columns names corresponding to three different sites. 
* :page_facing_up: `data_contributor_4`: Three *.csv* files where the two first files contains data for the same site but for two different years, and the third file contains substrate codes.
* :page_facing_up: `data_contributor_5`: Three *.xlsx* files where the two first files contains data in wide format with different columns names, and the third file contains site coordinates.


### 2.4 Variables selected

The first step of the workflow is to select the variables that will have to be present in the final synthetic dataset. The variables selected for the first case study are described in the **Table 1**.

**Table 1.** Variables selected for the benthic synthetic dataset. The icons for the variables categories (`Cat.`) represents :memo: = description variables, :globe_with_meridians: = spatial variables, :calendar: = temporal variables, :straight_ruler: = methodological variables, :crab: = taxonomic variables, :chart_with_upwards_trend: = metric variables. Variables names in parentheses correspond to the [DarwinCore (DwC) terms](https://dwc.tdwg.org/terms/).

|      | Variable (DwC)                  | Cat.                       | Type    | Unit | Description                              |
| ---- | ------------------------------- | -------------------------- | ------- | ---- | ---------------------------------------- |
| 1    | DatasetID (*datasetID*)         | :memo:                     | Factor  |      | Dataset ID                               |
| 2    | Area (*higherGeography*)        | :globe_with_meridians:     | Factor  |      | Biogeographic area                       |
| 3    | Country (*country*)             | :globe_with_meridians:     | Factor  |      | Country                                  |
| 4    | Archipelago (*islandGroup*)     | :globe_with_meridians:     | Factor  |      | Archipelago                              |
| 5    | Location (*stateProvince*)      | :globe_with_meridians:     | Factor  |      | Location or island within the country    |
| 6    | Site (*locality*)               | :globe_with_meridians:     | Factor  |      | Site within the location                 |
| 7    | Replicate                       | :globe_with_meridians:     | Integer |      | Replicate ID                             |
| 8    | Zone (*habitat*)                | :globe_with_meridians:     | Factor  |      | Reef zone                                |
| 9    | Latitude (*decimalLatitude*)    | :globe_with_meridians:     | Numeric |      | Latitude of the site (*decimal format*)  |
| 10   | Longitude (*decimalLongitude*)  | :globe_with_meridians:     | Numeric |      | Longitude of the site (*decimal format*) |
| 11   | Depth                           | :globe_with_meridians:     | Numeric | m    | Mean depth                               |
| 12   | Year (*year*)                   | :calendar:                 | Integer |      | Year                                     |
| 13   | Date (*eventDate*)              | :calendar:                 | Date    |      | Date (*YYYY-MM-DD*)                      |
| 14   | Method (*samplingProtocol*)     | :straight_ruler:           | Factor  |      | Description of the method used           |
| 15   | Observer                        | :straight_ruler:           | Factor  |      | Name of the diver                        |
| 16   | Category                        | :crab:                     | Factor  |      | See **Table 2**                          |
| 17   | Group                           | :crab:                     | Factor  |      | See **Table 2**                          |
| 18   | Family (*family*)               | :crab:                     | Factor  |      | Family                                   |
| 19   | Genus (*genus*)                 | :crab:                     | Factor  |      | Genus                                    |
| 20   | Species (*scientificName*)      | :crab:                     | Factor  |      | Species                                  |
| 21   | Cover (*measurementValue*)      | :chart_with_upwards_trend: | Numeric | %    | Cover percentage                         |


**Table 2.** Factor levels of variables `Category` and `Group` used for the re-categorization.

| Category            | Group            |
| -----------------   | ---------------  |
| Abiotic             | Rock             |
|                     | Rubble           |
|                     | Sand             |
|                     | Silt             |
| Algae               | Coralline algae  |
|                     | Cyanophyceae     |
|                     | Macroalgae       |
|                     | Turf algae       |
| Hard bleached coral |                  |
| Hard dead coral     |                  |
| Hard living coral   |                  |
| Other fauna         | Actiniaria       |
|                     | Alcyonacea       |
|                     | Antipatharia     |
|                     | Asteroidea       |
|                     | Bivalvia         |
|                     | Bryozoa          |
|                     | Corallimorpharia |
|                     | Crinoidea        |
|                     | Echinoidea       |
|                     | Gastropoda       |
|                     | Holothuroidea    |
|                     | Hydrozoa         |
|                     | Ophiuroidea      |
|                     | Polychaeta       |
|                     | Porifera         |
|                     | Tunicata         |
|                     | Zoantharia       |
| Seagrass            |                  |


## 3. Path 3.B - Taxonomical verification


### 3.1 Context

The second case study correspond to the path 3B of the workflow and illustrate the integration of data from monitoring of fish communities (vagile organisms) in coral reefs. Because the monitoring of fish is based on true taxonomical levels (*e.g.* species, genus) instead of broad categories, a taxonomical verification must be assessed during the data integration to avoid misspelling names and include recent update in taxonomy. We highlight that the different datasets were created to illustrate the worklow and they do not correspond to any existing real datasets.


### 3.2 Project organization

The folder `path_3b` contains the folders `data` and `R`. The `data` folder regroup all the data files with a numbering corresponding to their level of advancement in the workflow. Hence, the folder `01_raw` contains the different raw data files as received by data contributors, the folder `02_reformatted` contains the individually reformatted datasets, the file *03_synthetic-dataset* correspond to the grouped data with taxonomic assignment done, and the file *04_final-synthetic-dataset* correspond to the final synthetic dataset. 

Those data files and folders numbering is used correspondingly in the `R` folder where three scripts are present. The first one (*step-2_individual-data-reformatting.Rmd*) correspond to the individual data reformatting (step 2 of the workflow) with one or more chunk code by data contributor. The second one (*step-3_data-grouping-tax-assignment.Rmd*) correspond to the data grouping and taxonomic assignment (step 3 of the workflow), and the last one (*step-4_quality-assurance-quality-control.Rmd*) correspond to the quality assurance and quality control (step 4 of the workflow). 

The *.Rmd* format (rmarkdown) was chosen for the different R scripts because it allows a better segmentation and annotation of the code and process (necessary for the step 2) and the exportation of code and output to an HTML file which may include interactive tables, plots and maps (necessary for steps 3 and 4). The HTML files can be opened with a search engine (*e.g.* Google Chrome) and an internet connection is necessary for the visualization of interactive maps.


### 3.3 Raw datasets description

The `01_raw` folder includes five folders corresponding to the data shared by five different data contributors. Each of them represent a specific case:

* :page_facing_up: `data_contributor_1`: One *.xlsx* file containing two sheets, the first one with the main data and the second one with the site coordinates.
* :page_facing_up: `data_contributor_2`: Two *.csv* files, the first contains the main data in wide format and the second the sites coordinates.
* :page_facing_up: `data_contributor_3`: One *.xlsx* file containing three sheets, the first contains the main data, the second the site coordinates and the third the species codes.
* :page_facing_up: `data_contributor_4`: Two files, one in *.xlsx* and one in *.csv*. The *.xlsx* file contains two sheets with same column names, corresponding to two different sites. The *.csv* file contains the site coordinates.
* :page_facing_up: `data_contributor_5`: Four *.xlsx* files with one sheet, the first three contains the main data with same column names for three different sites, the fourth contains sites coordinates data.


### 3.4 Variables selected

The first step of the workflow is to select the variables that will have to be present in the final synthetic dataset. The variables selected for the second case study are described in the **Table 3**.

**Table 3.** Variables selected for the fish synthetic dataset. The factor levels of the variable `Size_type` are *Total length*, *Fork length* and *Standard length*. The icons for the variables categories (`Cat.`) represents :memo: = description variables, :globe_with_meridians: = spatial variables, :calendar: = temporal variables, :straight_ruler: = methodological variables, :crab: = taxonomic variables, :chart_with_upwards_trend: = metric variables.Variables names in parentheses correspond to the [DarwinCore (DwC) terms](https://dwc.tdwg.org/terms/).

|      | Variable (DwC)                   |  Cat.                      | Type    | Unit             | Description                              |
| ---- | -------------------------------- | -------------------------- | ------- | ---------------- | ---------------------------------------- |
| 1    | DatasetID (*datasetID*)          | :memo:                     | Factor  |                  | Dataset ID                               |
| 2    | Area (*higherGeography*)         | :globe_with_meridians:     | Factor  |                  | Biogeographic area                       |
| 3    | Country (*country*)              | :globe_with_meridians:     | Factor  |                  | Country                                  |
| 4    | Archipelago (*islandGroup*)      | :globe_with_meridians:     | Factor  |                  | Archipelago                              |
| 5    | Location (*stateProvince*)       | :globe_with_meridians:     | Factor  |                  | Location or island within the country    |
| 6    | Site (*locality*)                | :globe_with_meridians:     | Factor  |                  | Site within the location                 |
| 7    | Replicate                        | :globe_with_meridians:     | Integer |                  | Replicate ID                             |
| 8    | Zone (*habitat*)                 | :globe_with_meridians:     | Factor  |                  | Reef zone                                |
| 9    | Latitude (*decimalLatitude*)     | :globe_with_meridians:     | Numeric |                  | Latitude of the site (*decimal format*)  |
| 10   | Longitude  (*decimalLongitude*)  | :globe_with_meridians:     | Numeric |                  | Longitude of the site (*decimal format*) |
| 11   | Depth                            | :globe_with_meridians:     | Numeric | m                | Mean depth                               |
| 12   | Year (*year*)                    | :calendar:                 | Integer |                  | Year                                     |
| 13   | Date (*eventDate*)               | :calendar:                 | Date    |                  | Date (*YYYY-MM-DD*)                      |
| 14   | Method (*samplingProtocol*)      | :straight_ruler:           | Factor  |                  | Description of the method used           |
| 15   | Observer                         | :straight_ruler:           | Factor  |                  | Name of the diver                        |
| 16   | Family (*family*)                | :crab:                     | Factor  |                  | Family                                   |
| 17   | Genus  (*genus*)                 | :crab:                     | Factor  |                  | Genus                                    |
| 18   | Species (*scientificName*)       | :crab:                     | Factor  |                  | Species                                  |
| 19   | Density                          | :chart_with_upwards_trend: | Numeric | n. ind. 100 m-2  | Number of individuals                    |
| 20   | Size                             | :chart_with_upwards_trend: | Numeric | cm               | Size of individuals                      |
| 21   | Size_type (*measurementType*)    | :straight_ruler:           | Factor  |                  | Size type used to measure the size       |


## 4. How to report issues?

Please report any bugs or issues [HERE](https://github.com/JWicquart/monitoring_workflow/issues).


## 5. Reproducibility parameters

```R
R version 4.1.0 (2021-05-18)
Platform: x86_64-w64-mingw32/x64 (64-bit)
Running under: Windows 10 x64 (build 18363)

Matrix products: default

locale:
[1] LC_COLLATE=French_France.1252  LC_CTYPE=French_France.1252    LC_MONETARY=French_France.1252
[4] LC_NUMERIC=C                   LC_TIME=French_France.1252    

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] Hmisc_4.5-0       Formula_1.2-4     survival_3.2-11   lattice_0.20-44   rfishbase_3.1.8  
 [6] leaflet_2.0.4.1   DT_0.18           formattable_0.2.1 lubridate_1.7.10  readxl_1.3.1     
[11] forcats_0.5.1     stringr_1.4.0     dplyr_1.0.6       purrr_0.3.4       readr_1.4.0      
[16] tidyr_1.1.3       tibble_3.1.2      ggplot2_3.3.4     tidyverse_1.3.1  

loaded via a namespace (and not attached):
 [1] fs_1.5.0            RColorBrewer_1.1-2  progress_1.2.2      httr_1.4.2          gh_1.3.0           
 [6] tools_4.1.0         backports_1.2.1     utf8_1.2.1          R6_2.5.0            rpart_4.1-15       
[11] DBI_1.1.1           colorspace_2.0-1    nnet_7.3-16         withr_2.4.2         tidyselect_1.1.1   
[16] gridExtra_2.3       prettyunits_1.1.1   curl_4.3.1          compiler_4.1.0      cli_2.5.0          
[21] rvest_1.0.0         htmlTable_2.2.1     xml2_1.3.2          scales_1.1.1        checkmate_2.0.0    
[26] digest_0.6.27       foreign_0.8-81      rmarkdown_2.9       base64enc_0.1-3     jpeg_0.1-8.1       
[31] pkgconfig_2.0.3     htmltools_0.5.1.1   dbplyr_2.1.1        fastmap_1.1.0       htmlwidgets_1.5.3  
[36] rlang_0.4.11        rstudioapi_0.13     generics_0.1.0      jsonlite_1.7.2      crosstalk_1.1.1    
[41] magrittr_2.0.1      Matrix_1.3-4        Rcpp_1.0.6          munsell_0.5.0       fansi_0.5.0        
[46] lifecycle_1.0.0     stringi_1.6.2       yaml_2.2.1          grid_4.1.0          crayon_1.4.1       
[51] haven_2.4.1         splines_4.1.0       hms_1.1.0           knitr_1.33          pillar_1.6.1       
[56] reprex_2.0.0        glue_1.4.2          evaluate_0.14       arkdb_0.0.12        latticeExtra_0.6-29
[61] data.table_1.14.0   modelr_0.1.8        vctrs_0.3.8         png_0.1-7           cellranger_1.1.0   
[66] gtable_0.3.0        assertthat_0.2.1    cachem_1.0.5        xfun_0.24           broom_0.7.7        
[71] memoise_2.0.0       cluster_2.1.2       ellipsis_0.3.2
```
