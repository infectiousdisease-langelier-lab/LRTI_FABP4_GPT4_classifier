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
R version 4.3.2 (2023-10-31)
Platform: aarch64-apple-darwin20 (64-bit)
Running under: macOS 15.3.1

Matrix products: default
BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib 
LAPACK: /Library/Frameworks/R.framework/Versions/4.3-arm64/Resources/lib/libRlapack.dylib;  LAPACK version 3.11.0

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

time zone: US/Pacific
tzcode source: internal

attached base packages:
[1] stats4    stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] pROC_1.18.5                 DESeq2_1.42.1               SummarizedExperiment_1.32.0
 [4] Biobase_2.62.0              MatrixGenerics_1.14.0       matrixStats_1.3.0          
 [7] GenomicRanges_1.54.1        GenomeInfoDb_1.38.8         IRanges_2.36.0             
[10] S4Vectors_0.40.2            BiocGenerics_0.48.1         patchwork_1.2.0            
[13] lubridate_1.9.3             forcats_1.0.0               stringr_1.5.1              
[16] dplyr_1.1.4                 purrr_1.0.2                 readr_2.1.5                
[19] tidyr_1.3.1                 tibble_3.2.1                ggplot2_3.5.1              
[22] tidyverse_2.0.0            

loaded via a namespace (and not attached):
 [1] gtable_0.3.5            xfun_0.44               lattice_0.22-6          tzdb_0.4.0             
 [5] vctrs_0.6.5             tools_4.3.2             bitops_1.0-7            generics_0.1.3         
 [9] parallel_4.3.2          fansi_1.0.6             pkgconfig_2.0.3         Matrix_1.6-5           
[13] lifecycle_1.0.4         GenomeInfoDbData_1.2.11 compiler_4.3.2          munsell_0.5.1          
[17] codetools_0.2-20        RCurl_1.98-1.14         pillar_1.9.0            crayon_1.5.2           
[21] BiocParallel_1.36.0     DelayedArray_0.28.0     abind_1.4-5             tidyselect_1.2.1       
[25] locfit_1.5-9.9          stringi_1.8.4           grid_4.3.2              colorspace_2.1-0       
[29] cli_3.6.2               SparseArray_1.2.4       magrittr_2.0.3          S4Arrays_1.2.1         
[33] utf8_1.2.4              withr_3.0.0             scales_1.3.0            timechange_0.3.0       
[37] XVector_0.42.0          hms_1.1.3               knitr_1.47              rlang_1.1.4            
[41] Rcpp_1.0.12             glue_1.7.0              rstudioapi_0.16.0       plyr_1.8.9             
[45] R6_2.5.1                zlibbioc_1.48.2       
```