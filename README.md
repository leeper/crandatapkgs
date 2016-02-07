# CRAN Data-only Packages #

This package provides a simple function that lists data-only packages (or those primarily offering built-in datasets) that are available on CRAN. It does this by subsetting the output of `avaialable.packages()` to return a data.frame of known data-heavy and data-only packages.

## Installation ##

The package will soon be available on [CRAN](http://cran.r-project.org/web/packages/crandatapkgs/) and can be installed directly in R using:

```R
install.packages("crandatapkgs")
```

The latest development version on GitHub can be installed using **devtools**:

```R
if(!require("devtools")){
    install.packages("devtools")
    library("devtools")
}
install_github("leeper/crandatapkgs")
```

[![CRAN Version](http://www.r-pkg.org/badges/version/crandatapkgs)](http://cran.r-project.org/package=crandatapkgs)
![Downloads](http://cranlogs.r-pkg.org/badges/crandatapkgs)
[![Travis-CI Build Status](https://travis-ci.org/leeper/crandatapkgs.png?branch=master)](https://travis-ci.org/leeper/crandatapkgs)
[![codecov.io](http://codecov.io/github/leeper/crandatapkgs/coverage.svg?branch=master)](http://codecov.io/github/leeper/crandatapkgs?branch=master)

## Examples ##

To retrieve a data.frame listing of these known packages in R, simply do:


```r
library("crandatapkgs")
options(repos = c("https://cloud.r-project.org"))
a <- available_data()

# data structure returned by `available_data()`
str(a)
```

```
## 'data.frame':	98 obs. of  9 variables:
##  $ Package        : chr  "agridata" "alr3" "alr4" "aplore3" ...
##  $ Version        : chr  NA "2.0.5" "1.0.5" "0.7" ...
##  $ License        : chr  NA "GPL (>= 2)" "GPL (>= 2)" "GPL-3" ...
##  $ Depends        : chr  NA "R (>= 2.1.1), car" "R (>= 2.1.1), car, effects" "R (>= 3.1.1)" ...
##  $ Imports        : chr  NA NA NA NA ...
##  $ Suggests       : chr  NA NA NA "knitr, MASS, vcdExtra, nnet, survival, pROC" ...
##  $ Enhances       : chr  NA NA NA NA ...
##  $ Type           : chr  "Data" "Supplement" "Supplement" "Supplement" ...
##  $ DataDescription: chr  "Agriculture" "" "" "" ...
```

```r
# one package listing from the response
a[1,]
```

```
##    Package Version License Depends Imports Suggests Enhances Type
## 1 agridata    <NA>    <NA>    <NA>    <NA>     <NA>     <NA> Data
##   DataDescription
## 1     Agriculture
```

## Contributing Known Packages ##

New packages can be added by creating a GitHub pull request that edits the [packages](https://github.com/leeper/crandatapkgs/blob/master/inst/packages/packages) comma-separated values file and adding a row for a package in the form of:

```
PackageName,Type,"Data Description"
```

where `Type` is either `Data` (for data-only packages) or `Supplement` (for packages that provide data supplements to other packages or texts). `Data Description` should be a double-quoted description of the kind of data found in the package.

