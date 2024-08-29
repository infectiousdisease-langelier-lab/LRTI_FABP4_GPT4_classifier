# Integrating a host gene biomarker with a large language model for diagnosis of lower respiratory tract infection

Authors: &dagger;Hoang Van Phan, &dagger;Natasha Spottiswoode, Emily C. Lydon, Victoria T. Chu, Adolfo Cuesta, Alexander D. Kazberouk, Natalie L. Richmond, Carolyn S. Calfee, Charles R. Langelier<br>
&dagger;equal contribution<br>

Preprint: https://www.medrxiv.org/content/10.1101/2024.08.28.24312732v1

## Introduction

In a [previous study](https://www.medrxiv.org/content/10.1101/2024.08.19.24312242v1), we showed that _FABP4_ is an inverse-biomarker of LRTI in both pediatric and adult critically ill patients. In other words, the gene _FABP4_ is expressed at a lower level in LRTI patients compared to no LRTI patients.

Large language models (LLMs) such as Generative Pre-trained Transformer 4 (GPT-4) have gathered much interest in its ability to analyze free-form text. In this study, we tested how well GPT-4 could analyze clinician notes and radiologist reads of chest x-ray (CXR) to diagnose LRTI in adult critically ill patients. Then, we integrated GPT-4 diagnosis with _FABP4_ in a logistic regression classifier, and found that their combination was much better at diagnosing LRTI than the individual diagnoses.

## Code

All analyses were done with R v4.3.2. The analyses and figures in the manuscript could be reproduced by running the script [classifier.Rmd](classifier.Rmd).
* Figure 2a: [all_confusion_matrix.svg](output/all_confusion_matrix.svg)
* Figure 2b: [both_mean_roc.svg](output/both_mean_roc.svg)
* Supp. Figure 1a: [all_confusion_matrix.svg](output/all_confusion_matrix.svg)
* Supp. Figure 1b: [gpt4-vs-naive.svg](output/gpt4-vs-naive.svg)

The 5-fold cross-validation results are available in [classifier_5fold_CV.csv](output/classifier_5fold_CV.csv). This file can also be reproduced by the script [classifier.Rmd](classifier.Rmd).

## sessionInfo

```{R}
R version 4.3.2 (2023-10-31)
Platform: aarch64-apple-darwin20 (64-bit)
Running under: macOS Sonoma 14.6.1

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
[13] ggalluvial_0.12.5           lubridate_1.9.3             forcats_1.0.0              
[16] stringr_1.5.1               dplyr_1.1.4                 purrr_1.0.2                
[19] readr_2.1.5                 tidyr_1.3.1                 tibble_3.2.1               
[22] ggplot2_3.5.1               tidyverse_2.0.0            

loaded via a namespace (and not attached):
 [1] tidyselect_1.2.1        vipor_0.4.7             farver_2.1.2            bitops_1.0-7           
 [5] RCurl_1.98-1.14         pracma_2.4.4            timechange_0.3.0        lifecycle_1.0.4        
 [9] magrittr_2.0.3          compiler_4.3.2          rlang_1.1.4             tools_4.3.2            
[13] utf8_1.2.4              knitr_1.47              S4Arrays_1.2.1          labeling_0.4.3         
[17] DelayedArray_0.28.0     plyr_1.8.9              abind_1.4-5             BiocParallel_1.36.0    
[21] withr_3.0.0             grid_4.3.2              fansi_1.0.6             colorspace_2.1-0       
[25] scales_1.3.0            cli_3.6.2               crayon_1.5.2            ragg_1.3.2             
[29] generics_0.1.3          rstudioapi_0.16.0       tzdb_0.4.0              readxl_1.4.3           
[33] ggbeeswarm_0.7.2        zlibbioc_1.48.2         splines_4.3.2           parallel_4.3.2         
[37] cellranger_1.1.0        XVector_0.42.0          vctrs_0.6.5             Matrix_1.6-5           
[41] hms_1.1.3               beeswarm_0.4.0          systemfonts_1.1.0       locfit_1.5-9.9         
[45] glue_1.7.0              codetools_0.2-20        stringi_1.8.4           gtable_0.3.5           
[49] munsell_0.5.1           pillar_1.9.0            GenomeInfoDbData_1.2.11 R6_2.5.1               
[53] textshaping_0.4.0       lattice_0.22-6          Rcpp_1.0.12             svglite_2.1.3          
[57] SparseArray_1.2.4       nlme_3.1-164            mgcv_1.9-1              xfun_0.44              
[61] pkgconfig_2.0.3        
```