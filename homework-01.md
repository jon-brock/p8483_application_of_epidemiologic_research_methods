Homework 01
================

**This assignment is due Sunday, February 3, 2019 at 23:59 to
CourseWorks.**

-   Any assignment uploaded past the due date will automatically receive
    10 points off.
-   Assignments turned in more than one week following the due date will
    not be accepted.

------------------------------------------------------------------------

### Introduction

This assignment uses data from the 2015-2016 survey cycles of the U.S.
National Health and Nutrition Examination Survey (NHANES). Please note
that these example analyses do not account for the complex survey design
of NHANES as these are beyond the scope of this course.

A description of the NHANES surveys can be found
[here](https://www.cdc.gov/nchs/nhanes/).

For this assignment, I am providing you with a SAS dataset that combines
information from several NHANES modules. The codebook for this dataset
is at the end of this document.

For this homework assignment we are going to be using several datasets
from the NHANES 2015-2016 survey that I have helpfully merged together.
You’ll be doing this yourself going forward. The relevant data file is
on CourseWorks and on SAS On Demand and is called `HW1_2019.sas7bdat`.

Note: for this assignment I modified the `age` variable and created a
new variable for language spoken at home.

------------------------------------------------------------------------

``` r
library(haven)
library(tidyverse)
```

#### Question 1

##### 6 points

-   (3 points) Create a LIBNAME statement telling SAS which folder your
    SAS data set is contained in.  
-   (3 points) Use a SAS command to make a copy of this data file into
    your temporary (“work”) folder. For the rest of the assignment, make
    sure you are using the ‘temporary’ SAS data file and not the
    original one.

``` r
hw1 <- read_sas('./data/hw1_2019.sas7bdat') %>% 
    janitor::clean_names()

head(hw1)
```

    ## # A tibble: 6 x 13
    ##    seqn riagendr bmxwt bmxht bmxbmi acd011a acd011b acd011c acd040 acd110
    ##   <dbl>    <dbl> <dbl> <dbl>  <dbl>   <dbl>   <dbl>   <dbl>  <dbl>  <dbl>
    ## 1 83758        1  NA     NA    NA         1      NA      NA     NA     NA
    ## 2 83773        2  67.7  150.   30.2       1      NA      NA     NA     NA
    ## 3 83791        2  78.6  168.   28         1      NA      NA     NA     NA
    ## 4 83801        2  58.5  157.   23.7       1      NA      NA     NA     NA
    ## 5 83818        2  72.3  159.   28.5      NA      NA      NA      1     NA
    ## 6 83821        1  79.8  166.   29.1       1      NA      NA     NA     NA
    ## # … with 3 more variables: other_language_at_home <dbl>, hiq011 <dbl>,
    ## #   age <dbl>

#### Question 2

##### 7 points

-   (2 points) How many **variables** are in the dataset (`hw1`)?

``` r
ncol(hw1)
```

    ## [1] 13

-   (2 points) How many **observations** are there in the dataset
    (`hw1`)?

``` r
nrow(hw1)
```

    ## [1] 9971
