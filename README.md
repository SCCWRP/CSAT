---
output:
  html_document:
    keep_md: yes
    toc: no
    self_contained: no
---

## CSAT

#### Maintainer: *Marcus W. Beck, marcusb@sccwrp.org*

The California Stream Assessment Toolbox is a combined package for the [CSCI](https://github.com/SCCWRP/CSCI) (California Stream Condition Index), [ASCI](https://github.com/SCCWRP/ASCI) (Algal Stream Condition Index), and [PHAB](https://github.com/SCCWRP/PHAB) (Physical Habitat index) indices.  The functionality of each index is the same in CSAT as in the original packages.  This package exists solely as a convenience for installation. 

### Installation

Install the package as follows:


```r
install.packages('devtools')
library(devtools)
install_github('SCCWRP/CSAT')
library(CSAT)
```

### Attribution

This package pillaged code extensively from [tidyverse](https://github.com/tidyverse/tidyverse).

