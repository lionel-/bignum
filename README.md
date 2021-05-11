
<!-- README.md is generated from README.Rmd. Please edit that file -->

# bignum

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/bignum)](https://CRAN.R-project.org/package=bignum)
[![R build
status](https://github.com/davidchall/bignum/workflows/R-CMD-check/badge.svg)](https://github.com/davidchall/bignum/actions)
[![Coverage
status](https://codecov.io/gh/davidchall/bignum/branch/master/graph/badge.svg)](https://codecov.io/gh/davidchall/bignum?branch=master)
<!-- badges: end -->

bignum provides numeric vectors with greater precision than R atomic
numeric vectors.

-   `biginteger()` stores any integer (i.e. arbitrary precision).
-   `bigfloat()` stores 50 decimal digits of precision.

They prioritize precision over performance, so computations are slower
than those using `integer()` or `double()`.

## Installation

You can install the development version from GitHub:

``` r
# install.packages("remotes")
remotes::install_github("davidchall/bignum")
```

## Usage

### Arbitrary-precision integer vector

The limited precision of atomic vectors introduces errors when working
with very large integers. As an example, let’s calculate the factorial
of 23. In base R, we’d calculate:

``` r
options(digits = 20)
factorial(23)
#> [1] 25852016738884978212864
```

The factorial of 23 includes a factor of 10, and so the final digit
*must* be zero. Using `biginteger()` yields the correct result:

``` r
prod(biginteger(1:23))
#> <biginteger[1]>
#> [1] 25852016738884976640000
```

### High-precision floating-point vector

`bigfloat()` vectors support much higher precision than `double()`
vectors:

``` r
1 / 3
#> [1] 0.33333333333333331483
bigfloat(1) / 3
#> <bigfloat[1]>
#> [1] 0.33333333333333333333333333333333333333333333333333
```

However, you need to be careful not to limit the precision accidentally:

``` r
bigfloat(1 / 3)
#> <bigfloat[1]>
#> [1] 0.333333333333333
```

------------------------------------------------------------------------

Please note that the bignum project is released with a [Contributor Code
of
Conduct](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to abide by its terms.
