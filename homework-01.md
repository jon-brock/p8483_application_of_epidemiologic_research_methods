Homework 01
================

-   [Introduction](#introduction)
-   [Question 1 - Data import](#question-1---data-import)
-   [Question 2 - Using `proc contents`, answer the following
    questions](#question-2---using-proc-contents-answer-the-following-questions)
-   [Question 3 - Using `proc print`, answer the following
    questions](#question-3---using-proc-print-answer-the-following-questions)

**This assignment is due Sunday, February 3, 2019 at 23:59 to
CourseWorks.**

-   Any assignment uploaded past the due date will automatically receive
    10 points off.
-   Assignments turned in more than one week following the due date will
    not be accepted.

------------------------------------------------------------------------

#### Introduction

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

------------------------------------------------------------------------

#### Question 1 - Data import

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

------------------------------------------------------------------------

#### Question 2 - Using `proc contents`, answer the following questions

##### 7 points

-   (2 points) How many **variables** are in the dataset?

``` r
ncol(hw1)
```

    ## [1] 13

-   (2 points) How many **observations** are there in the dataset?

``` r
nrow(hw1)
```

    ## [1] 9971

-   (3 points) ~~Write the necessary SAS code to ensure that the
    variable names are presented in their order of appearance in the
    dataset.~~

------------------------------------------------------------------------

#### Question 3 - Using `proc print`, answer the following questions

##### 22 points

-   (2 points) ~~What does the column “Obs” refer to?~~

-   (5 points) Write a SAS code to print the first 50 observations of
    the following variables (one code displaying all three variables and
    nothing else). ~~REMOVE THE PRINTOUT OF THE “OBS” column in your SAS
    code~~:

    1.  Age (variable name “`age`”)  
    2.  Language primarily spoken at home (variable name
        “`other_language_at_home`”)  
    3.  Body Mass Index (variable name “`bmxbmi`”)

``` r
hw1 %>% 
    select(age, other_language_at_home, bmxbmi) %>% 
    head(n = 50) %>% 
    knitr::kable(align = 'c')
```

| age | other\_language\_at\_home | bmxbmi |
|:---:|:-------------------------:|:------:|
| 84  |             0             |   NA   |
| 93  |             0             |  30.2  |
| 82  |             0             |  28.0  |
| 80  |             0             |  23.7  |
| 89  |             1             |  28.5  |
| 88  |             0             |  29.1  |
| 81  |             0             |  24.2  |
| 80  |             0             |   NA   |
| 88  |             1             |  20.1  |
| 87  |             0             |  23.5  |
| 81  |             0             |   NA   |
| 93  |             0             |  26.9  |
| 97  |             0             |  26.0  |
| 82  |             0             |  20.8  |
| 83  |             0             |  34.6  |
| 86  |             1             |  25.5  |
| 82  |             1             |  20.3  |
| 90  |             0             |  29.4  |
| 84  |             1             |  27.2  |
| 87  |             0             |  24.1  |
| 81  |             0             |  21.8  |
| 97  |             0             |  18.0  |
| 92  |             0             |  27.6  |
| 86  |             0             |  26.6  |
| 84  |             0             |  23.7  |
| 80  |             0             |  24.0  |
| 82  |             0             |  32.1  |
| 82  |             0             |  29.9  |
| 80  |             1             |  29.1  |
| 88  |             0             |  26.2  |
| 81  |             0             |  22.9  |
| 84  |             0             |  19.9  |
| 80  |             0             |  40.3  |
| 81  |             1             |  25.1  |
| 88  |             1             |  38.8  |
| 83  |             0             |  30.9  |
| 92  |             0             |  25.2  |
| 83  |             0             |  25.8  |
| 88  |             0             |  33.4  |
| 86  |             0             |  24.4  |
| 92  |             1             |  22.4  |
| 93  |             1             |  22.6  |
| 81  |             0             |  29.8  |
| 87  |             0             |  26.3  |
| 88  |             1             |  22.2  |
| 83  |             0             |  26.6  |
| 84  |             0             |  25.9  |
| 84  |             0             |  30.0  |
| 83  |             1             |  31.2  |
| 89  |             0             |  20.8  |

-   (5 points) Write a SAS code to print observations from observation
    500 to observation 550 of the following variables ~~while changing
    the orientation of the variable name headings to vertical~~:
    1.  Age (variable name “`age`”)  
    2.  Language primarily spoken at home (variable name
        “`other_language_at_home`”)  
    3.  Body Mass Index (variable name “`bmxbmi`”)

``` r
hw1 %>% slice(500:549)
```

    ## # A tibble: 50 x 13
    ##     seqn riagendr bmxwt bmxht bmxbmi acd011a acd011b acd011c acd040 acd110
    ##    <dbl>    <dbl> <dbl> <dbl>  <dbl>   <dbl>   <dbl>   <dbl>  <dbl>  <dbl>
    ##  1 83863        1  95.8  176.   31.1      NA      NA      NA      2     NA
    ##  2 83864        1  19.5  112.   15.7       1      NA      NA     NA     NA
    ##  3 83865        2  39.7  156.   16.3       1      NA      NA     NA     NA
    ##  4 83866        1  88    169.   30.7       1      NA      NA     NA     NA
    ##  5 83867        1  72.3  174.   23.9       1      NA      NA     NA     NA
    ##  6 83868        2  43.2  146.   20.4      NA      NA      NA      5     NA
    ##  7 83869        2  61.3  160.   23.9       1      NA      NA     NA     NA
    ##  8 83870        1  82.4  170.   28.6      NA      NA      NA      2     NA
    ##  9 83871        2  53.7  140.   27.4      NA      NA      NA      1     NA
    ## 10 83872        1  67.2  170    23.3      NA      NA      NA      2     NA
    ## # … with 40 more rows, and 3 more variables: other_language_at_home <dbl>,
    ## #   hiq011 <dbl>, age <dbl>

-   (5 points for code, 1 for answer) - Write a SAS code to print out
    all of the data for individuals aged greater than or equal to 50
    years of age (using the age variable named “`age`”). How many
    observations are there?

``` r
# It is unreasonable to print the entire output - only the first ten observations are printed  
hw1 %>% 
    filter(age >= 50) %>% 
    head() %>% 
    knitr::kable(align = 'c')
```

| seqn  | riagendr | bmxwt | bmxht | bmxbmi | acd011a | acd011b | acd011c | acd040 | acd110 | other\_language\_at\_home | hiq011 | age |
|:-----:|:--------:|:-----:|:-----:|:------:|:-------:|:-------:|:-------:|:------:|:------:|:-------------------------:|:------:|:---:|
| 83758 |    1     |  NA   |  NA   |   NA   |    1    |   NA    |   NA    |   NA   |   NA   |             0             |   1    | 84  |
| 83773 |    2     | 67.7  | 149.8 |  30.2  |    1    |   NA    |   NA    |   NA   |   NA   |             0             |   1    | 93  |
| 83791 |    2     | 78.6  | 167.6 |  28.0  |    1    |   NA    |   NA    |   NA   |   NA   |             0             |   1    | 82  |
| 83801 |    2     | 58.5  | 157.1 |  23.7  |    1    |   NA    |   NA    |   NA   |   NA   |             0             |   1    | 80  |
| 83818 |    2     | 72.3  | 159.2 |  28.5  |   NA    |   NA    |   NA    |   1    |   NA   |             1             |   1    | 89  |
| 83821 |    1     | 79.8  | 165.7 |  29.1  |    1    |   NA    |   NA    |   NA   |   NA   |             0             |   1    | 88  |

``` r
# There are 2825 observations  
hw1 %>% 
    filter(age >= 50) %>% 
    count()
```

    ## # A tibble: 1 x 1
    ##       n
    ##   <int>
    ## 1  2825

-   (5 points for code, 1 for answer) - Write a SAS code to print out
    all of the data for individuals aged greater than or equal to 50
    years of age (using the age variable named “`age`”) **AND** who have
    missing data for the variable Body Mass Index (variable name
    “`bmxbmi`”). How many observations are there?
