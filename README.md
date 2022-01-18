# Readme-for-ZIG-Harmonization

Date created: 2021 September 20

README FOR DE EYTO FEEAGH DATA

This document details the data cleaning and harmonization procedure performed for the Zooplankton as Indicators working group (ZIG). It is meant to highlight major cleaning steps taken to make the dataset compatible with other submitted dataset. Any questions about the larger ZIG project can be submitted to:

Steph Figary (sef92@cornell.edu)
Michael Meyer (michael.f.meyer@wsu.edu)
Warren Currie (warren.currie@dfo-mpo.gc.ca)
This submitted dataset was cleaned by Lia Ivanick (lia.ivanick@uvm.edu).


Cleaning Script and Session Info
The script 000a_deeyto_feeagh_livanick.R was used to check data values, correct values formats, and generally assess the data for outliers. This scripts requires:

Inputs: This script requires the submitted Obertegger input data file CORRECTED_ZIG_data_deeyto_feeagh - Elvira de Eyto.xlsx.

Outputs: This script outputs the following files to the directory data/derived_products/deeyto_feeagh_disaggregated:

additional_data_deeyto.csv
equipment_clean_deeyto.csv
lake_information_deeyto.csv
lake_timeline_deeyto.csv
station_information_deeyto.csv
taxa_list_deeyto.csv
zooplankton_abundance_deeyto.csv
zooplankton_length_deeyto.csv
water_parameters_deeyto.csv


The script requires the following directory tree:
|───data
│   ├───derived_products
│   │   └───deeyto_feeagh_disaggregated
│   └───inputs
├───figures
│   └───deeyto_feeagh_qc
└───scripts


The following session information describes the computational environment, in which the cleaning procedure occurred.

R version 3.6.3 (2020-02-29)
Platform: x86_64-apple-darwin15.6.0 (64-bit)
Running under: macOS Mojave 10.14.6

Matrix products: default
BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib
LAPACK: /Library/Frameworks/R.framework/Versions/3.6/Resources/lib/libRlapack.dylib

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] janitor_2.1.0   readxl_1.3.1    forcats_0.5.1   stringr_1.4.0   dplyr_1.0.7    
 [6] purrr_0.3.4     readr_2.0.1     tidyr_1.1.3     tibble_3.1.4    ggplot2_3.3.5  
[11] tidyverse_1.3.1

loaded via a namespace (and not attached):
 [1] Rcpp_1.0.7       cellranger_1.1.0 pillar_1.6.2     compiler_3.6.3  
 [5] dbplyr_2.1.1     tools_3.6.3      jsonlite_1.7.2   lubridate_1.7.10
 [9] lifecycle_1.0.0  gtable_0.3.0     pkgconfig_2.0.3  rlang_0.4.11    
[13] reprex_2.0.1     cli_3.0.1        rstudioapi_0.13  DBI_1.1.1       
[17] haven_2.4.3      xml2_1.3.2       withr_2.4.2      httr_1.4.2      
[21] fs_1.5.0         generics_0.1.0   vctrs_0.3.8      hms_1.1.0       
[25] grid_3.6.3       tidyselect_1.1.1 snakecase_0.11.0 glue_1.4.2      
[29] R6_2.5.1         fansi_0.5.0      tzdb_0.1.2       modelr_0.1.8    
[33] magrittr_2.0.1   backports_1.2.1  scales_1.1.1     ellipsis_0.3.2  
[37] rvest_1.0.1      assertthat_0.2.1 colorspace_2.0-2 utf8_1.2.2      
[41] stringi_1.7.4    munsell_0.5.0    broom_0.7.9      crayon_1.4.1




NOTES FROM LIA IVANICK WHILE CLEANING DE EYTO DATASET

Lake Information
-Lake comments are not type character because they are hard coded as NAs

Water Parameters
-time_hhm was originally given as "between 09:00 and 16:00" --> changed to NA
-no data for NO2NO3_mgL, do_hypo_mgL, alkalinity_mgL, silica_mgL, hardness_mgL, dissolved_P_ugL, DIC_um, TKN_mgL, chloride_mgL
-changed the following parameters from class character/numeric (NAs introduced by coercion)--> class double: surface_chla_ug_l, NO2NO3_mgL, TKN_mgL,conductivity_umho_cm , chloride_mgL, turbidity_NTU, surface_tp_ug_l ,silica_mgL, do_epi_mgL, DOC_um, TN_mgL, surface_ph, secchi_depth_m, thermocline_depth , dissolved_P_ugL, do_hypo_mgL, DIC_um, hardness_mgL
- Changed surface_chla_ug_l zeros to 0.5 ug/l
- Changed do_epi_mg_l zeros to NA

Taxa List
-invasive column is not type character because invasive is hard coded as NAs

Zooplankton Abundance
*50 or so warnings loading csv
-changed biomass_units "NA" --> NA
-change time_hhm from "between 09:00 and 16:00" --> NA
-Change time_zone from "GMT" --> o

Equipment
- Change the following to type character in equipment_clean:
TKN_method
Silica_method
Hardness_method
dissolved_P_method
Chloride_method
NO2NO3_method 
DIC_method
alkalinity_method
- No method because no data was collected:
NO2NO3_mgL
silica_mgL
dissolved_P_ugL
TKN_mgL
DIC_um
chloride_mgL
alkalinity_mgL
hardness_mgL


