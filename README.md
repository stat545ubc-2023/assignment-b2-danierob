
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
devtools::install_github("stat545ubc-2023/")
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

    count_all_missing_by_group(airquality, Month)

Cool. You can do the same thing but pipe %\>% it if thats more your
speed.

    airquality %>% 
      count_all_missing_by_group(Month) 

One more! The optional `.groups` argument allows us to keep the output
grouped by the grouping column.

    count_all_missing_by_group(airquality, Month, .groups = "keep")
