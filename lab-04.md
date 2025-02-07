Lab 04 - Visualizing spatial data. La Quinta is Spanish for next to
Denny’s, Pt. 1
================
Yuxin Xie
2/7/25

### Load packages and data

``` r
#install.packages("devtools")
#devtools::install_github("rstudio-education/dsbox")
library(tidyverse) 
library(dsbox) 
```

``` r
Dennys <- dsbox::dennys
Laquinta <- dsbox::laquinta
states <- read_csv("data/states.csv")
```

### Exercise 1

``` r
cat ("There are", nrow (Dennys), "rows and", ncol(Dennys), "variables in the Dennys dataset.", "\n") 
```

    ## There are 1643 rows and 6 variables in the Dennys dataset.

``` r
###There are six variables: address, city, state, zip code, longitude, and latitude. Each row represents one Denny's store. 
```

### Exercise 2

``` r
cat ("There are", nrow (Laquinta), "rows and", ncol(Laquinta), "variables in the Laquinta dataset.", "\n") 
```

    ## There are 909 rows and 6 variables in the Laquinta dataset.

``` r
###There are six variables: address, city, state, zip code, longitude, and latitude. Each row represents one La Quinta store. 
```

### Exercise 3

``` r
## from the website, La Quinta has some stores across the world, for instance, in South America: Chile, Colombia, Ecuador. In Asia: China. In Europe: Turkey. 
## All Danny's stores are in the US.
```

### Exercise 4

``` r
##Denny's 
non_us_states_dennys<-setdiff(states$abbreviation, Dennys$state)
print(non_us_states_dennys)
```

    ## character(0)

``` r
##all Denny's stores are in the US

##La Quinta 
non_us_states_LaQ<-setdiff(Laquinta$state, states$abbreviation)
print(non_us_states_LaQ)
```

    ##  [1] "AG"  "QR"  "CH"  "NL"  "ANT" "ON"  "VE"  "PU"  "SL"  "FM"  "BC"

``` r
## There are stores in "AG"  "QR"  "CH"  "NL"  "ANT" "ON"  "VE"  "PU"  "SL"  "FM"  "BC" outside of the US. 
```

### Exercise 5

``` r
##Denny's locations outside the US
Dennys %>%
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 0 × 6
    ## # ℹ 6 variables: address <chr>, city <chr>, state <chr>, zip <chr>,
    ## #   longitude <dbl>, latitude <dbl>

``` r
##Note that the %in% operator matches the states listed in the state variable to those listed in states$abbreviation. The ! operator means not. 
```

### Exercise 6

### Exercise 7

### Exercise 8

### Exercise 9

### Exercise 10

### Exercise 11

### Exercise 12
