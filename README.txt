This is a readme file for the analyses used in the paper by GM Walter entitled: "Experimental evidence that phenotypic evolution but not plasticity occurs along genetic lines of least resistance in homogeneous environments"

This readme file describes in detail:
A) The datafile
B) The objects (.Rdata files) needed to run the R code
C) The versions of all packages used in the R code


A) The datafile
Data for this paper was sourced from the data file (DRYADyeamanchenwhitlock2010rawdata.csv) that is in the published Dryad repository:

Yeaman, S., C. Yukon, and M. C. Whitlock. 2010b. Data from: No effect of environmental heterogeneity on the maintenance of genetic variation in wing shape in Drosophila melanogaster. Dryad, Dataset, https://doi.org/10.5061/dryad.1719.

The only differences with the data used in the current paper ("Data_foranimalmodel.csv") and that of the original repository is:
1) Inclusion of columns, such as sire and dam, which make it possible to construct the pedigree
2) Inclusion of only the 5 traits of interest that are analysed in the current paper, and in Yeaman et al. (2010).
3) Some additional identifier columns for sex and generation

Brief descriptions for the 18 columns in the datafile:

row: unique row
ImageID: unique identifiers for each fly wing image
treatment: 6 levels corresponding to Fig. 1a
replicate: 5 replicate populations / treatment
FSF: Full-sibling family uniquely labelled within each replicate cage (1-5) and assay (d=cold, u=hot)
GEN: Generation (parent vs offspring)
gen_code: sire (s), dam (d), female offspring (f), male offspring (m)
sex: female (f) and male (m)
id: unique individual. For the parent generation, in the form of treatment+replicate_assay_FSF+dam/sire so that, for example, c1_d_1d = cold treatment - cage 1_cold assay_family 1 - dam (for that family). The offspring are labelled in numerical sequence starting from 1.
dam: id of the dam for each individual. (NA for the parents as their parents are unknown).
sire: id of the sire fore each individual.
assay: flies reared in cold condition (d) or warm condition (u)
TRAITS (see Fig 1b):-
centroid: wing size
line9.10: distance between landmarks 9 and 10
angle7.8.9: angle between landmarks 7, 8, and 9
angle3.10.4: angle between landmarks 3, 10 and 4
angle 2.4.8: angle between landmarks 2, 4 and 8
treatment2: Numerical version for treatment (1-6).


B) Objects used by the R script "A2_SupplementaryCode.Rmd"

The R code uses mean G (average for each treatment) that are stored in the folder "G_observed" and G for the replicate cages, stored in the folder "G_observed_replicatecages". Although the model outputs could not all be included (due to file size and number of files) their outputs have been constructed and saved in a convenient .Rdata file for the R-code to use. The R-code also details how all outputs (models and arrays) were created.

Below these folders are described in detail:

- Folder "G_observed" contains the output for the 12 implementations of equation 1 for each treatment in both assays (n=12). These implementations were used to compare with averaging directly across G estimated for all replicate cages.

- Folder "G_observed_replicatecages" contains: 1) All 60 G-matrices saved as a .csv file (All_G-Matrices.csv), and 2) Three .Rdata files that contain the arrays for genetic (G), maternal (M) and residual (R) matrices in the form of nxnxmxMCMC (where m=60).

The object "G_Random_Tensor.Rdata" contains null G (see the R-code for how this was constructed). This is in the form of nxnxmxNRAN (where m=12 for all six treatments in both assays; NRAN=500 for the number of randomisations that were conducted to construct null G).

C) Package versions
R version 4.0.5 (2021-03-31)Platform: x86_64-apple-darwin17.0 (64-bit)Running under: macOS Big Sur 10.16Matrix products: defaultLAPACK: /Library/Frameworks/R.framework/Versions/4.0/Resources/lib/libRlapack.dyliblocale:[1] en_AU.UTF-8/en_AU.UTF-8/en_AU.UTF-8/C/en_AU.UTF-8/en_AU.UTF-8attached base packages:[1] stats     graphics  grDevices utils     datasets  methods   base     other attached packages: [1] data.table_1.14.0 SimDesign_2.3     tidyr_1.1.3       gridExtra_2.3     ggplot2_3.3.6     dplyr_1.0.6       [7] gdata_2.18.0      MCMCglmm_2.32     ape_5.5           coda_0.19-4       Matrix_1.3-2      matrixcalc_1.0-3 [13] MASS_7.3-54      loaded via a namespace (and not attached): [1] gtools_3.8.2      tidyselect_1.1.1  xfun_0.22         purrr_0.3.4       pbapply_1.4-3     lattice_0.20-41   [7] colorspace_2.0-1  vctrs_0.3.8       generics_0.1.0    htmltools_0.5.1.1 yaml_2.2.1        utf8_1.2.1       [13] rlang_0.4.10      pillar_1.6.0      glue_1.4.2        withr_2.4.2       DBI_1.1.1         plyr_1.8.6       [19] foreach_1.5.1     lifecycle_1.0.0   munsell_0.5.0     gtable_0.3.0      codetools_0.2-18  evaluate_0.14    [25] knitr_1.32        parallel_4.0.5    fansi_0.4.2       Rcpp_1.0.6        corpcor_1.6.9     scales_1.1.1     [31] tensorA_0.36.2    digest_0.6.27     grid_4.0.5        tools_4.0.5       magrittr_2.0.1    tibble_3.1.1     [37] crayon_1.4.1      pkgconfig_2.0.3   ellipsis_0.3.2    assertthat_0.2.1  rmarkdown_2.8     iterators_1.0.13 [43] cubature_2.0.4.1  R6_2.5.0          nlme_3.1-152      compiler_4.0.5   