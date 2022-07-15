Sales
================
Naomi Ekas

``` r
library(tidyverse)
library(readxl)
```

-   Read in the Excel file called `sales.xlsx` from the `data-raw/`
    folder such that it looks like the following.

<img src="images/sales-1.png" width="20%" />

``` r
sales <- read_excel("data-raw/sales.xlsx", skip = 3, col_names = c("id", "n"))
```

-   **Stretch goal:** Manipulate the sales data such such that it looks
    like the following.

<img src="images/sales-2.png" width="25%" />

``` r
sales <- sales %>% 
  mutate(is_brand_name = str_detect(id, "Brand"))
```

``` r
sales <- sales %>% 
  mutate(is_brand_name = str_detect(id, "Brand"),
         brand = if_else(is_brand_name, id, NULL )) 
```

``` r
sales <- sales %>% 
  mutate(is_brand_name = str_detect(id, "Brand"),
         brand = if_else(is_brand_name, id, NULL )) %>% 
  fill(brand)
```

``` r
sales <- sales %>% 
  mutate(is_brand_name = str_detect(id, "Brand"),
         brand = if_else(is_brand_name, id, NULL )) %>% 
  fill(brand) %>% 
  filter(!is_brand_name) %>% 
  select(brand, id, n)
```
