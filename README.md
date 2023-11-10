
<!-- README.md is generated from README.Rmd. Please edit that file -->

## count

<!-- badges: start -->
<!-- badges: end -->

count is a package created for STAT 545 assignment B2, making an R
package. This package contains functions that can aid in data analysis
and data organization.

#### Installation

You can install the development version of count from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("stat545ubc-2023/count", "ref = 0.1.0")
```

#### Functions

The only function currently in count is the count_all_missing_by_group
function.

#### What the function?

count_all_missing_by_group is a function that counts missing values for
all columns by group, providing a summary tibble of missing value
(i.e. NAs) as output. This function is valuable for early assessments of
data, spot-checking for missing values among levels and categories.

#### Examples

I know you’re eager, so here is the function in action:

Let’s count up all the missing values in the airquality dataset by the
Month variable:

``` r
count::count_all_missing_by_group(airquality, Month)
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

Cool. You can do the same thing but pipe \|\> (base R) or %\>% (dplyr)
it if that’s more your speed.

``` r
airquality |> 
  count::count_all_missing_by_group(Month) 
#> # A tibble: 5 × 6
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```

One more! The optional `.groups` argument allows us to keep the output
grouped by the grouping column.

``` r
count::count_all_missing_by_group(airquality, Month, .groups = "keep")
#> # A tibble: 5 × 6
#> # Groups:   Month [5]
#>   Month Ozone Solar.R  Wind  Temp   Day
#>   <int> <int>   <int> <int> <int> <int>
#> 1     5     5       4     0     0     0
#> 2     6    21       0     0     0     0
#> 3     7     5       0     0     0     0
#> 4     8     5       3     0     0     0
#> 5     9     1       0     0     0     0
```
