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

*1. What are the dimensions of the `Denny’s` dataset? (Hint: Use inline
R code and functions like `nrow` and `ncol` to compose your answer.)
What does each row in the dataset represent? What are the variables?*

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

*2. What are the dimensions of the La Quinta’s dataset? What does each
row in the dataset represent? What are the variables?*

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

We would like to limit our analysis to Denny’s and La Quinta locations
in the United States.

*3. Take a look at the websites that the data come from. Are there any
La Quinta’s locations outside of the US? If so, which countries? What
about Denny’s?*

There are both La Quinta’s in Mexico, Canada, China, New Zealand,
Honduras, Turkey, UAE, Chile, and Columbia.

There are actually Denny’s in Canada, Mexico, Costa Rica, Chile,
Honduras, El Salvador, the United Kingdom, New Zealand, according to
Google.

*4. Now take a look at the data. What would be some ways of determining
whether or not either establishment has any locations outside the US
using just the data (and not the websites). Don’t worry about whether
you know how to implement this, just brainstorm some ideas. Write down
at least one as your answer, but you’re welcomed to write down a few
options too.*

One way would be to look for `state` responses that are not U.S. states,
likely returning as NA. Alternatively, if you hated your free time, you
could do the same by accounting for all possible U.S. Zip codes.
Likewise, if you hated your free time even more you could account for
the borders of the U.S. by `latitude` and `longitude` and look for
responses that fail to fall within those criteria.

*5. Find the Denny’s locations that are outside the US, if any. To do
so, filter the Denny’s locations for observations where `state` is not
in `states$abbreviation`. The code for this is given below. Note that
the `%in%` operator matches the states listed in the state variable to
those listed in `states$abbreviation`. The `!` operator means not. Are
there any Denny’s locations outside the US?*

``` r
dennys %>%
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 0 x 6
    ## # ... with 6 variables: address <chr>, city <chr>, state <chr>, zip <chr>,
    ## #   longitude <dbl>, latitude <dbl>

This turned up no Denny’s outside the U.S.

*6. Add a country variable to the Denny’s dataset and set all
observations equal to `"United States"`. Remember, you can use the
`mutate` function for adding a variable. Make sure to save the result of
this as dennys again so that the stored data frame contains the new
variable going forward.*

``` r
dennys <- dennys %>%
  mutate(country = "United States")
```

*7. Find the La Quinta locations that are outside the US, and figure out
which country they are in. This might require some googling. Take notes,
you will need to use this information in the next exercise.*

``` r
laquinta %>%
  filter(!(state %in% states$abbreviation)) %>%
    view()
```

There are 11 in Mexico, 2 in Canada, and 1 in Colombia.

*8. Add a country variable to the La Quinta dataset. Use the case\_when
function to populate this variable. You’ll need to refer to your notes
from Exercise 7 about which country the non-US locations are in. Here is
some starter code to get you going:*

``` r
laquinta <- laquinta %>%
  mutate(country = case_when(
    state %in% state.abb ~ "United States",
    state %in% c("ON", "BC") ~ "Canada",
    state == "ANT"           ~ "Colombia",
    state %in% c("AG", "QR", "CH", "NL", "VE", "PU", "SL", "FM") ~ "Mexico"
  ))
```
