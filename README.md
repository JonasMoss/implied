
<!-- README.md is generated from README.Rmd. Please edit that file -->

<!-- badges: start -->

[![AppVeyor build
status](https://ci.appveyor.com/api/projects/status/github/opisthokonta/implied?branch=master&svg=true)](https://ci.appveyor.com/project/opisthokonta/implied)
[![Travis build
status](https://travis-ci.org/opisthokonta/implied.svg?branch=master)](https://travis-ci.org/opisthokonta/implied)
[![Codecov test
coverage](https://codecov.io/gh/JonasMoss/implied/branch/master/graph/badge.svg)](https://codecov.io/gh/JonasMoss/implied?branch=master)
[![Project Status: WIP – Initial development is in progress, but there
has not yet been a stable, usable release suitable for the
public.](https://www.repostatus.org/badges/latest/wip.svg)](https://www.repostatus.org/#wip)
<!-- badges: end -->

## implied

This package converts bookmaker odds into proper probabilities with the
function `implied_probabilities`. Currently six methods are available,
each of them with different assumptions about how the bookmakers convert
their probabilities into odds.

The natural conversion of bookmaker odds into probabilities is to take
the inverse of the odds. This procedure has two serious problems:

1.  The converted probabilities are not proper, as they can sum to more
    than one. The excess probability is called the *bookmaker margin*.
2.  The converted probabilities will be biased due to [favorite-longshot
    bias](https://en.wikipedia.org/wiki/Favourite-longshot_bias). This
    happens even if the bookmaker margin is accounted for.

The methods in this package remove the bookmaker margin and some of them
also adjust for favorite-longshot bias.

## Installation

Install the package using `devtools` from inside `R`.

``` r
install.packages("devtools")
devtools::install_github("opisthokonta/implied")
```

## Usage

A bookmaker provides the odds 4.20 for home, 3.70 for a draw, and 1.95
for away. To calculate the implied probabilities for these odds using
the `basic` method call:

``` r
library(implied)

# method = c("basic", "shin", "wpo", "or", "power", "additive")
implied_probabilities(c(4.20, 3.70, 1.95), method = "basic")
#> $probabilities
#>           [,1]      [,2]      [,3]
#> [1,] 0.2331556 0.2646631 0.5021813
#> 
#> $margin
#> [1] 0.02118602
#> 
#> $problematic
#> [1] FALSE
```

## Documentation

See the [overview
vignette](https://github.com/ophistokonta/implied/vignettes/overview)
for an overview of the package, including a description of the methods
used to calculate implied probabilities.

## How to Contribute or Get Help

If you encounter a bug, have a feature request or need some help, open a
[Github issue](https://github.com/ophistokonta/implied/issues). Create a
pull requests to contribute. This project follows a [Contributor Code of
Conduct](https://www.contributor-covenant.org/version/1/4/code-of-conduct.md).
