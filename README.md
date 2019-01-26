# A guide to reproducibility scientific computing and analysis

This is a (non-comprehensive, very personally biased) guide to reproducibilty in scientific computing, software design and usage, data management and analysis. I focus primarily on programming and analysis practices in R, but the principles I've learned are extensible to your tool of choice. I also talk about general data management, and open-science platforms.

**WIP**

## Guiding principles for reproducible R analyses

1. Do not alter another machine's state
2. Do not refer to things unique to your machine, or that are likely to differ between machines
3. Record **everything** that can affect the analysis
4. R-scripts (`.R`-files) should be able to run from top to bottom hitch-free (as far as possible)

## Bad vs good R practices for reproducibility

Bad R                                        | Good R
---------------------------------------------|-----------------------------------------------------------------
`setwd("my/path/that/no-one/else/has/)`      | Using R-projects (i.e. a `.Rproj`-file)
`read.csv("an/absolute/path/")`              | `here::here("relative/path/")`
`rm(list = ls()`                             | **Don't use this in R-scripts**
`install.package(...)`                       | **Don't use this in R-script**
`important_random_nos <- runif(...)`         | `set.seed(1234); reproducible_random_nos <- runif(...)`
