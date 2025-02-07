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
D <- dsbox::dennys
LQ <- dsbox::laquinta
states <- read_csv("data/states.csv")
```

### Exercise 1

``` r
cat ("There are", nrow (D), "rows and", ncol(D), "variables in the Dennys dataset.", "\n") 
```

    ## There are 1643 rows and 6 variables in the Dennys dataset.

``` r
###There are six variables: address, city, state, zip code, longitude, and latitude. Each row represents one Denny's store. 
```

### Exercise 2

``` r
cat ("There are", nrow (LQ), "rows and", ncol(LQ), "variables in the Laquinta dataset.", "\n") 
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
non_us_states_D<-setdiff(states$abbreviation, D$state)
print(non_us_states_D)
```

    ## character(0)

``` r
##all Denny's stores are in the US

##La Quinta 
non_us_states_LQ<-setdiff(LQ$state, states$abbreviation)
print(non_us_states_LQ)
```

    ##  [1] "AG"  "QR"  "CH"  "NL"  "ANT" "ON"  "VE"  "PU"  "SL"  "FM"  "BC"

``` r
## There are stores in "AG"  "QR"  "CH"  "NL"  "ANT" "ON"  "VE"  "PU"  "SL"  "FM"  "BC" outside of the US. 
```

### Exercise 5

``` r
##Denny's locations outside the US
D %>%
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 0 × 6
    ## # ℹ 6 variables: address <chr>, city <chr>, state <chr>, zip <chr>,
    ## #   longitude <dbl>, latitude <dbl>

``` r
##Note that the %in% operator matches the states listed in the state variable to those listed in states$abbreviation. The ! operator means not. 
```

### Exercise 6

``` r
D_US<-D %>%
  mutate(country = "United States")
## D_US<-will assign the result to D_US, if just run dn %>%
  #mutate(country = "United States"), It modifies the dataset temporarily but does not save the changes. 
```

### Exercise 7

``` r
LQ_NUS<-LQ %>%
  filter(!(state %in% states$abbreviation))
print (LQ_NUS$state)
```

    ##  [1] "AG"  "QR"  "CH"  "NL"  "ANT" "NL"  "NL"  "ON"  "VE"  "PU"  "PU"  "SL" 
    ## [13] "FM"  "BC"

``` r
print (LQ_NUS$address)
```

    ##  [1] "Carretera Panamericana Sur KM 12"                                       
    ##  [2] "Av. Tulum Mza. 14 S.M. 4 Lote 2"                                        
    ##  [3] "Ejercito Nacional 8211"                                                 
    ##  [4] "Blvd. Aeropuerto 4001"                                                  
    ##  [5] "Carrera 38 # 26-13 Avenida las Palmas con Loma de San Julian El Poblado"
    ##  [6] "AV. PINO SUAREZ No. 1001"                                               
    ##  [7] "Av. Fidel Velazquez #3000 Col. Central"                                 
    ##  [8] "63 King Street East"                                                    
    ##  [9] "Calle Las Torres-1 Colonia Reforma"                                     
    ## [10] "Blvd. Audi N. 3 Ciudad Modelo"                                          
    ## [11] "Ave. Zeta del Cochero No 407"                                           
    ## [12] "Av. Benito Juarez 1230 B (Carretera 57) Col. Valle Dorado Zona Hotelera"
    ## [13] "Blvd. Fuerza Armadas"                                                   
    ## [14] "8640 Alexandra Rd"

``` r
print (LQ_NUS$zip)
```

    ##  [1] "20345"  "77500"  "32528"  "66600"  "050016" "64000"  "64190"  "L1H1B4"
    ##  [9] "93210"  "75010"  "72810"  "78399"  "11101"  "V6X1C4"

``` r
## countries: Mexico, Colombia, Canada, and Honduras
## Mexico: AG, QR, CH, NL, VE, PU, SL, 
## Colombia: ANT
## Canada: ON, BC
## Honduras: FM
```

### Exercise 8

### Exercise 9

### Exercise 10

### Exercise 11

### Exercise 12
