---
output:
  html_document:
    keep_md: yes
    toc: no
    self_contained: no
---

## CSAT

#### Maintainer: *Marcus W. Beck, marcusb@sccwrp.org*

The California Stream Assessment Toolbox is a combined package for the [CSCI](https://github.com/SCCWRP/CSCI) (California Stream Condition Index), [ASCI](https://github.com/SCCWRP/ASCI) (Algal Stream Condition Index), and [PHAB](https://github.com/SCCWRP/PHAB) (Physical Habitat index) packages.  The functionality of each index is the same in CSAT as in the original packages.  This package exists solely as a convenience for installation. 

## Installation

Install the package as follows:


```r
install.packages('devtools')
library(devtools)
install_github('SCCWRP/CSAT')
library(CSAT)
```

## Usage

`library(CSAT)` will load the core CSAT packages:

* [CSCI](https://github.com/SCCWRP/CSCI), California Stream Condition Index. 
* [ASCI](https://github.com/SCCWRP/ASCI), Algal Stream Condition Index.
* [PHAB](https://github.com/SCCWRP/PHAB), for Physical Habitat index.

You will receive startup messages indicating the pacckages are being loaded:


```r
library(CSAT)
```

```
## -- Attaching packages --------------------------------------- CSAT 0.0.1 --
```

```
## v CSCI 1.1.2          v ASCI 0.0.1     
## v CSCI 1.1.2          v PHAB 0.0.1.9004
```

### CSCI


```r
data(bugs_stations)
results <- CSCI(bugs = bugs_stations[[1]], stations = bugs_stations[[2]])
ls(results)
```

```
## [1] "core"        "Suppl1_grps" "Suppl1_mmi"  "Suppl1_OE"   "Suppl2_mmi" 
## [6] "Suppl2_OE"
```

### ASCI


```r
data(demo_algae_tax)
data(demo_algae_sitedata)
demo_results <- ASCI(taxain = demo_algae_tax, sitein = demo_algae_sitedata)
demo_results
```

```
## An object of class asci 
## Scores calculated for diatoms, sba, hybrid indices for 4 unique samples
## Use these functions for access: perf, scores, Supp1_mmi, Supp1_OE, Supp2_OE
```

```r
scores(demo_results)
```

```
## # A tibble: 12 x 8
##    taxa    SampleID              MMI MMI_Perc~     O     E Oove~ OoverE_P~
##  * <chr>   <chr>               <dbl>     <dbl> <dbl> <dbl> <dbl>     <dbl>
##  1 diatoms 000CAT148_8/10/10_1 0.813    0.898   8.00  6.67 1.20      0.676
##  2 diatoms 102PS0139_8/9/10_1  0.740    0.254   8.00  7.05 1.13      0.310
##  3 diatoms 105DLCDCC_5/19/09_1 0.777    0.622   8.00  6.41 1.25      0.874
##  4 diatoms 105DLCDCC_6/23/09_1 0.731    0.179   7.00  6.41 1.09      0.134
##  5 hybrid  000CAT148_8/10/10_1 0.691    0.917   9.00  9.64 0.934     0.200
##  6 hybrid  102PS0139_8/9/10_1  0.540    0.202  10.0  10.3  0.966     0.290
##  7 hybrid  105DLCDCC_5/19/09_1 0.554    0.268   9.00  8.76 1.03      0.494
##  8 hybrid  105DLCDCC_6/23/09_1 0.601    0.528  10.0   8.41 1.19      0.921
##  9 sba     000CAT148_8/10/10_1 0.733    0.701   1.00  2.33 0.429     0.106
## 10 sba     102PS0139_8/9/10_1  0.636    0.466   2.00  2.82 0.709     0.760
## 11 sba     105DLCDCC_5/19/09_1 0.435    0.0860  3.00  5.39 0.556     0.360
## 12 sba     105DLCDCC_6/23/09_1 0.795    0.822   4.00  5.43 0.737     0.816
```

### PHAB


```r
data(stations)
data(phab)
IPI(stations = stations, phab = phab)
```

```
##   StationCode SampleDate       PHAB_SampleID  IPI IPI_percentile
## 1   105PS0107  9/14/2009 105PS0107_9/14/2009 1.16           0.90
## 2   205PS0157  6/19/2012 205PS0157_6/19/2012 1.04           0.62
## 3   305PS0057  6/16/2009 305PS0057_6/16/2009 0.79           0.04
## 4   504PS0147  6/23/2008 504PS0147_6/23/2008 0.78           0.03
## 5   632PS0007  7/23/2008 632PS0007_7/23/2008 1.10           0.79
## 6   901PS0057  5/14/2008 901PS0057_5/14/2008 1.08           0.74
##   Ev_FlowHab Ev_FlowHab_score H_AqHab H_AqHab_pred H_AqHab_score H_SubNat
## 1       0.85             0.89    1.59         1.11          1.00     1.57
## 2       0.96             1.00    1.42         1.35          0.80     1.41
## 3       0.50             0.51    1.32         1.42          0.70     0.49
## 4       0.28             0.28    1.24         1.30          0.72     0.98
## 5       0.90             0.95    1.51         1.41          0.82     1.80
## 6       0.70             0.73    1.52         1.38          0.84     1.80
##   H_SubNat_score PCT_SAFN PCT_RC PCT_SAFN_pred PCT_SAFN_score XCMG
## 1           0.83        6      0         24.60           1.00   99
## 2           0.74       51      2         22.06           0.40  131
## 3           0.26       83      0         29.51           0.12  152
## 4           0.52        1      0         34.38           1.00   55
## 5           0.95       14      0         13.49           0.79  126
## 6           0.95       40      3         34.46           0.69  122
##   XCMG_pred XCMG_score IPI_qa Ev_FlowHab_qa H_AqHab_qa H_SubNat_qa
## 1     93.64       0.78   1.00             1          1           1
## 2    104.72       0.90   1.00             1          1           1
## 3    106.05       1.00   1.00             1          1           1
## 4     95.41       0.51   1.00             1          1           1
## 5    123.10       0.76   1.00             1          1           1
## 6    102.16       0.86   0.95             1          1           1
##   PCT_SAFN_qa XCMG_qa
## 1           1    1.00
## 2           1    1.00
## 3           1    1.00
## 4           1    1.00
## 5           1    1.00
## 6           1    0.95
```

## Attribution

This package pillaged code from [tidyverse](https://github.com/tidyverse/tidyverse).

