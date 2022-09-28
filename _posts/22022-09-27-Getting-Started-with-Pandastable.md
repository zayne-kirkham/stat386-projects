---
layout: post
title:  "Getting Started with Pandastable"
date:   2022-09-27
author: Zayne Kirkham
description: This is a cool project
image: 
---


---
layout: post
title: Posting Rmarkdowns to your Jekyll website
output:
  md_document:
    variant: gfm
    preserve_yaml: true
---

# Test chunk 1

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.4 
    ## ✔ tibble  3.1.7      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.4.0 
    ## ✔ readr   2.1.2      ✔ forcats 0.5.1

    ## Warning: package 'ggplot2' was built under R version 4.2.1

    ## Warning: package 'tidyr' was built under R version 4.2.1

    ## Warning: package 'dplyr' was built under R version 4.2.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
head(starwars)
```

    ## # A tibble: 6 × 14
    ##   name      height  mass hair_color skin_color eye_color birth_year sex   gender
    ##   <chr>      <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
    ## 1 Luke Sky…    172    77 blond      fair       blue            19   male  mascu…
    ## 2 C-3PO        167    75 <NA>       gold       yellow         112   none  mascu…
    ## 3 R2-D2         96    32 <NA>       white, bl… red             33   none  mascu…
    ## 4 Darth Va…    202   136 none       white      yellow          41.9 male  mascu…
    ## 5 Leia Org…    150    49 brown      light      brown           19   fema… femin…
    ## 6 Owen Lars    178   120 brown, gr… light      blue            52   male  mascu…
    ## # … with 5 more variables: homeworld <chr>, species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>

# chunk 2

``` r
diamonds %>% filter(color=='E')
```

    ## # A tibble: 9,797 × 10
    ##    carat cut       color clarity depth table price     x     y     z
    ##    <dbl> <ord>     <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1  0.23 Ideal     E     SI2      61.5    55   326  3.95  3.98  2.43
    ##  2  0.21 Premium   E     SI1      59.8    61   326  3.89  3.84  2.31
    ##  3  0.23 Good      E     VS1      56.9    65   327  4.05  4.07  2.31
    ##  4  0.22 Fair      E     VS2      65.1    61   337  3.87  3.78  2.49
    ##  5  0.2  Premium   E     SI2      60.2    62   345  3.79  3.75  2.27
    ##  6  0.32 Premium   E     I1       60.9    58   345  4.38  4.42  2.68
    ##  7  0.23 Very Good E     VS2      63.8    55   352  3.85  3.92  2.48
    ##  8  0.23 Very Good E     VS1      60.7    59   402  3.97  4.01  2.42
    ##  9  0.23 Very Good E     VS1      59.5    58   402  4.01  4.06  2.4 
    ## 10  0.23 Good      E     VS1      64.1    59   402  3.83  3.85  2.46
    ## # … with 9,787 more rows


