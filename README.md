
<!-- README.md is generated from README.Rmd. Please edit that file -->

# panelWranglR

<!-- badges: start -->

[![Travis build
status](https://travis-ci.org/JSzitas/panelWranglR.svg?branch=master)](https://travis-ci.org/JSzitas/panelWranglR)
[![Lifecycle:
stable](https://img.shields.io/badge/lifecycle-stable-green.svg)](https://www.tidyverse.org/lifecycle/#stable)
[![License: GPL
v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![CRAN
status](https://www.r-pkg.org/badges/version/panelWranglR)](https://CRAN.R-project.org/package=panelWranglR)
<!-- badges: end -->

**panelWranglR** is a simple package for wrangling panel data.

## Installation

You can install the stable version of panelWranglR from
[CRAN](https://CRAN.R-project.org) with

``` r
install.packages("panelWranglR")
```

The latest version is also available from
[github](https://github.com/JSzitas/panelWranglR) using the *devtools*
package

``` r
devtools::install_github("JSzitas/panelWranglR")
```

## Introduction

The goal of **panelWranglR** is to provide simple functions that take
care of common panel data wrangling needs, such as lagging a panel,
differencing a panel (including selections of variables from a panel),
finding correlations/autocorrelations in a panel, and so on. For a full
list of all of the available functionality, please refer to the
documentation.

## Example

Let’s start by lagging a whole panel of data, using 5 lags.

``` r
# example data: 
    X <- matrix(rnorm(800000),8000,100)
    tim <- seq(1:4000)
    geo_AT <- rep(c("AT"), length = 4000)
    geo_NO <- rep(c("NO"), length = 4000)
    both_vec_1 <- cbind(tim,geo_NO)
    both_vec_2 <- cbind(tim,geo_AT)
    both <- rbind(both_vec_1,both_vec_2)
    X <- cbind(both,X)
    colnames(X) <- c("time", "geo", paste("V", 1:100, sep = "")) 

library(panelWranglR)

    panel_lag( data = X, 
               cross.section = "geo",
               time.variable = "time",
               lags = 5 )    
    
```

Or maybe we want to turn the cross section variable into several dummy
variables:

``` r
panel_dummify( data = X,
               cross.section = "geo" )
```

We can do that for the time variable too (though it is not recommended
with many time ‘levels’\!)

Further functionality follows the same general syntax and usage (and
documentation hopefully clears up any misunderstandings.)

## Contributing

If you would like to contribute a pull request, please do contribute\!
All contributions will be considered for acceptance, provided they are
justifiable and the code is reasonable, regardless of anything related
to the person submitting the pull request. Please keep things civil -
there is no need for negativity. Also, please do refrain from adding
unnecessary dependencies (*Ex:* pipe) to the package (such pull requests
as would add an unnecessary dependency will be denied/ suspended until
the code can be made dependency free).
