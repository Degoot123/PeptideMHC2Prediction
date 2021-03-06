<!-- README.md is generated from README.Rmd. Please edit that file -->
PeptideMHC2Prediction
=====================

An R package implementing biophysical methods for prediction of peptide and MHC-II molecules interactions, developed by Degoot and colleagues (<https://www.frontiersin.org/articles/10.3389/fimmu.2018.01410/full>). It can predict the probability of binding affinity between peptide of any length that greater than or equal 9 and 35 HLA-II molecules belonging to the three MHC-II loci of human genes: DRB, DP, and DQ.

License
-------

This package is licensed under a CC BY-NC-SA 4.0 license. It is free to use for non-commercial purposes.

Installation
------------

``` r
# Install the package from github
# devtools::install_github("Degoot/PeptideMHC2Prediction")
```

Example
=======

Load the package

``` r
 ## library(PeptideMHC2Prediction)
```

To predict probability of binding affinity between peptide, for example say,

``` r
  pep <- "ADAGYAPATPAAAGA"
```

and an MHC-II molecule, for examples say DRB1\_0401, based on trans-allelic method, you can use the following:

``` r
##predictBinding(pep, "DRB1_0401", "DRB", 2)
```

Or using the intra-allelic method as follows:

``` r
##predictBinding(pep, "DRB1_0401", "DRB", 1)
```

the package also allows to make predictions for set of peptides and MHC-II molecules, together organized in form of a dataframe of the three columns. The columns of the dataframe must be in the following order: th peptide, the name of MHC-II moleclue, and the locus. For example, let us assume that we have a dataframe called **dataset**, which has the following structure.

|     Peptide     |     MHC    | Locus |
|:---------------:|:----------:|:-----:|
| AAAGAEAGKATTEEQ | DRB1\_0301 |  DRB  |
| AFALVLLFCALASSC | DRB3\_0101 |  DRB  |
| AAAGAEAGKATTEEQ | DRB1\_1501 |  DRB  |
| SGLVWGQKYFKGNFQ |  DPB10401  |   DP  |
| SSNPTILSEGNSFTA |  DQB10201  |   DQ  |

Then you call the function **predictBindingSet** to get prediction of the above dataset as follows:

``` r
##predictBindingSet(dataset, opt = 1)
```

The parameter opt specifies the prediction method, 1 for intra-allelic method and 2 for trans-allelic method. The output of function **predictBindingSet** is a dataframe of four columns, which has the below structure:

|     Peptide     |     MHC    | Probability | Binary Value |
|:---------------:|:----------:|:-----------:|:------------:|
| AAAGAEAGKATTEEQ | DRB1\_0301 |    0.176    |       0      |
| AFALVLLFCALASSC | DRB3\_0101 |    0.549    |       1      |
| AAAGAEAGKATTEEQ | DRB1\_1501 |    0.679    |       1      |
| SGLVWGQKYFKGNFQ |  DPB10401  |    0.300    |       0      |
| SSNPTILSEGNSFTA |  DQB10201  |    0.026    |       0      |

References
----------

Abdoelnaser M. Degoot, Chirove Faraimunashe, and Ndifon Wilfred (2018) Trans-Allelic Model for Prediction of Peptide:MHC-II Interactions, Frontiers in Immunology. URL:<https://www.frontiersin.org/article/10.3389/fimmu.2018.01410>.
