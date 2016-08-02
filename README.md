# CRAN Data-only Packages #

This package provides a simple function that lists data-only packages (or those primarily offering built-in datasets) that are available on CRAN. It does this by subsetting the output of `avaialable.packages()` to return a data.frame of known data-heavy and data-only packages.

To retrieve a data.frame listing of these known packages in R, simply do:


```r
library("crandatapkgs")
options(repos = c("https://cloud.r-project.org"))
a <- available_data()

# data structure returned by `available_data()`
str(a)
```

```
## 'data.frame':	98 obs. of  5 variables:
##  $ Package        : chr  "agridata" "alr3" "alr4" "aplore3" ...
##  $ Version        : chr  NA "2.0.5" "1.0.5" "0.7" ...
##  $ License        : chr  NA "GPL (>= 2)" "GPL (>= 2)" "GPL-3" ...
##  $ Type           : chr  "Data" "Supplement" "Supplement" "Supplement" ...
##  $ DataDescription: chr  "Agriculture" "" "" "" ...
```

```r
# a few packages from the response
a[1:3,]
```

```
##    Package Version    License       Type DataDescription
## 1 agridata    <NA>       <NA>       Data     Agriculture
## 2     alr3   2.0.5 GPL (>= 2) Supplement                
## 3     alr4   1.0.5 GPL (>= 2) Supplement
```

## Contributing Known Packages ##

New packages can be added by creating a GitHub pull request that edits the [packages](https://github.com/leeper/crandatapkgs/blob/master/inst/packages/packages) comma-separated values file and adding a row for a package in the form of:

```
PackageName,Type,"Data Description"
```

where `Type` is either `Data` (for data-only packages) or `Supplement` (for packages that provide data supplements to other packages or texts). `Data Description` should be a double-quoted description of the kind of data found in the package.


## Installation ##

[![CRAN Version](http://www.r-pkg.org/badges/version/crandatapkgs)](https://cran.r-project.org/package=crandatapkgs)
![Downloads](http://cranlogs.r-pkg.org/badges/crandatapkgs)
[![Travis-CI Build Status](https://travis-ci.org/leeper/crandatapkgs.png?branch=master)](https://travis-ci.org/leeper/crandatapkgs)
[![codecov.io](http://codecov.io/github/leeper/crandatapkgs/coverage.svg?branch=master)](http://codecov.io/github/leeper/crandatapkgs?branch=master)

The package is available on [CRAN](https://cran.r-project.org/package=crandatapkgs) and can be installed directly in R using:

```R
install.packages("crandatapkgs")
```

The latest development version on GitHub can be installed using **ghit**:

```R
if(!require("ghit")){
    install.packages("ghit")
}
ghit::install_github("leeper/crandatapkgs")
```

