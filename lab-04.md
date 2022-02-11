Lab 04 - La Quinta is Spanish for next to Denny’s, Pt. 1
================
Adam Paul
2/11

### Load packages and data

``` r
library(tidyverse) 
```

``` r
states <- read_csv("data/states.csv")
load("data/dennys.rda")
load("data/laquinta.rda")
```

> Getting this to work took a lot longer than I wanted to, until I
> finally realized the problem was that I hadn’t called the data within
> my markdown. It was running but not knitting.

### Exercise 1

1.  What are the dimensions of the `Denny’s` dataset? (Hint: Use inline
    R code and functions like `nrow` and `ncol` to compose your answer.)
    What does each row in the dataset represent? What are the variables?

bind\_rows(dennys)

``` r
glimpse(dennys)
```

    ## Rows: 1,643
    ## Columns: 6
    ## $ address   <chr> "2900 Denali", "3850 Debarr Road", "1929 Airport Way", "230 ~
    ## $ city      <chr> "Anchorage", "Anchorage", "Fairbanks", "Auburn", "Birmingham~
    ## $ state     <chr> "AK", "AK", "AK", "AL", "AL", "AL", "AL", "AL", "AL", "AL", ~
    ## $ zip       <chr> "99503", "99508", "99701", "36849", "35207", "35294", "35056~
    ## $ longitude <dbl> -149.8767, -149.8090, -147.7600, -85.4681, -86.8317, -86.803~
    ## $ latitude  <dbl> 61.1953, 61.2097, 64.8366, 32.6033, 33.5615, 33.5007, 34.206~

There are 1,643 rows, which are each an entry of denny’s locations.
There are six columns, indicating “address”, “city”, “state”,
“zip-code”, “longitude”, and “latitude.”

``` r
glimpse(laquinta)
```

    ## Rows: 909
    ## Columns: 6
    ## $ address   <chr> "793 W. Bel Air Avenue", "3018 CatClaw Dr", "3501 West Lake ~
    ## $ city      <chr> "\nAberdeen", "\nAbilene", "\nAbilene", "\nAcworth", "\nAda"~
    ## $ state     <chr> "MD", "TX", "TX", "GA", "OK", "TX", "AG", "TX", "NM", "NM", ~
    ## $ zip       <chr> "21001", "79606", "79601", "30102", "74820", "75254", "20345~
    ## $ longitude <dbl> -76.18846, -99.77877, -99.72269, -84.65609, -96.63652, -96.8~
    ## $ latitude  <dbl> 39.52322, 32.41349, 32.49136, 34.08204, 34.78180, 32.95164, ~

There are 909 rows, indicating each listed La Quinta and its associated
variable responses. There are six columns, all the same as Denny’s;
indicating “address”, “city”, “state”, “zip-code”, “longitude”, and
“latitude.”

### Exercise 2

Remove this text, and add your answer for Exercise 2 here. Add code
chunks as needed. Don’t forget to label your code chunk. Do not use
spaces in code chunk labels.

### Exercise 3

…

### Exercise 4

…

### Exercise 5

…

### Exercise 6

…

Add exercise headings as needed.
