# Integrating a host transcriptomic biomarker with a large language model for diagnosis of lower respiratory tract infection

Authors: Hoang Van Phan&dagger;, Natasha Spottiswoode&dagger;, Emily C. Lydon, Victoria T. Chu, Adolfo Cuesta, Alexander D. Kazberouk, Natalie L. Richmond, Carolyn S. Calfee, Charles R. Langelier<br>
&dagger;equal contribution<br>

Preprint: https://www.medrxiv.org/content/10.1101/2024.08.28.24312732v1 (older version of the manuscript)

## Introduction

In a [previous study](https://www.atsjournals.org/doi/abs/10.1164/rccm.202403-0516RL), we showed that _FABP4_ is a transcriptomic inverse-biomarker of LRTI in both pediatric and adult critically ill patients. In other words, the gene _FABP4_ is expressed at a lower level in LRTI patients compared to no LRTI patients.

Large language models (LLMs) such as Generative Pre-trained Transformer 4 (GPT-4) have gathered much interest in its ability to analyze free-form text. In this study, we tested how well GPT-4 could analyze clinician notes and radiologist reads of chest x-ray (CXR) to diagnose LRTI in adult critically ill patients. Then, we integrated GPT-4 diagnosis with _FABP4_ in a logistic regression classifier, and found that their combination was much better at diagnosing LRTI than the individual diagnoses.

We first tested our method in the discovery cohort, called mBAL. After this, we tested the method in an independent validation cohort, called COMET.

## Hardware and run time

The code was run on an M1 Pro Macbook with 16GB of RAM. We expect each R markdown notebook takes fewer than 5 minutes to run.

## Code

All analyses were done with R v4.3.2. The analyses and figures in the manuscript could be reproduced by running the script [classifier.Rmd](classifier.Rmd).
* Figure 2A: [discovery_all_confusion_matrix.svg](output/discovery_all_confusion_matrix.svg)
* Figure 2B: [discovery_both_mean_roc.svg](output/discovery_both_mean_roc.svg)
* Figure 2C: [validation_all_confusion_matrix.svg](output/validation_all_confusion_matrix.svg)
* Figure 2D: [validation_both_mean_roc.svg](output/validation_both_mean_roc.svg)
* Figure 3A: [discovery_all_confusion_matrix.svg](output/discovery_all_confusion_matrix.svg)
* Figure 3B: [discovery_gpt4-vs-naive.svg](output/discovery_gpt4-vs-naive.svg)

The 5-fold cross-validation results of the discovery cohort are available in [discovery_classifier_5fold_CV.csv](output/discovery_classifier_5fold_CV.csv). This file can also be reproduced by the script [discovery_cohort.Rmd](discovery_cohort.Rmd).

The 3-fold cross-validation results of the validation cohort are available in [validation_classifier_3fold_CV.csv](output/validation_classifier_3fold_CV.csv). This file can also be reproduced by the script [validation_cohort.Rmd](validation_cohort.Rmd).

## Other folders

* Folder `gene_counts`: contains the gene counts tables. Note that the `discover_counts.csv` file contains data for samples that are not analyzed (they were adjudicated to have Suspected LRTI or Indeterminate)

* Folder `metadata`: contains the metadata files.

* Folder `output`: contains the outputs of the codes, including the figures.

## R session info

```{R}
R version 4.5.0 (2025-04-11)
Platform: aarch64-apple-darwin20
Running under: macOS Sequoia 15.6

Matrix products: default
BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib 
LAPACK: /Library/Frameworks/R.framework/Versions/4.5-arm64/Resources/lib/libRlapack.dylib;  LAPACK version 3.12.1

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

time zone: US/Pacific
tzcode source: internal

attached base packages:
[1] stats4    stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] pROC_1.19.0.1               DESeq2_1.48.1               SummarizedExperiment_1.38.1 Biobase_2.68.0              MatrixGenerics_1.20.0       matrixStats_1.5.0          
 [7] GenomicRanges_1.60.0        GenomeInfoDb_1.44.1         IRanges_2.42.0              S4Vectors_0.46.0            BiocGenerics_0.54.0         generics_0.1.4             
[13] patchwork_1.3.1             lubridate_1.9.4             forcats_1.0.0               stringr_1.5.1               dplyr_1.1.4                 purrr_1.1.0                
[19] readr_2.1.5                 tidyr_1.3.1                 tibble_3.3.0                ggplot2_3.5.2               tidyverse_2.0.0            

loaded via a namespace (and not attached):
 [1] gtable_0.3.6            bslib_0.9.0             xfun_0.52               lattice_0.22-7          tzdb_0.5.0              vctrs_0.6.5             tools_4.5.0            
 [8] parallel_4.5.0          pkgconfig_2.0.3         Matrix_1.7-3            RColorBrewer_1.1-3      lifecycle_1.0.4         GenomeInfoDbData_1.2.14 compiler_4.5.0         
[15] farver_2.1.2            textshaping_1.0.1       codetools_0.2-20        sass_0.4.10             htmltools_0.5.8.1       yaml_2.3.10             jquerylib_0.1.4        
[22] pillar_1.11.0           crayon_1.5.3            BiocParallel_1.42.1     cachem_1.1.0            DelayedArray_0.34.1     abind_1.4-8             digest_0.6.37          
[29] tidyselect_1.2.1        locfit_1.5-9.12         stringi_1.8.7           labeling_0.4.3          fastmap_1.2.0           grid_4.5.0              cli_3.6.5              
[36] SparseArray_1.8.1       magrittr_2.0.3          S4Arrays_1.8.1          withr_3.0.2             scales_1.4.0            UCSC.utils_1.4.0        timechange_0.3.0       
[43] rmarkdown_2.29          XVector_0.48.0          httr_1.4.7              ragg_1.4.0              hms_1.1.3               evaluate_1.0.4          knitr_1.50             
[50] rlang_1.1.6             Rcpp_1.1.0              glue_1.8.0              svglite_2.2.1           rstudioapi_0.17.1       jsonlite_2.0.0          R6_2.6.1               
[57] systemfonts_1.2.3      
```