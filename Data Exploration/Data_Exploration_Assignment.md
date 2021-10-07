Data Exploration Assignment for Heartland Family Service's Data
=
### - Piyush Basia

* Initializing the ggplot2 library in R-studio and loading the data from "HFS Service Data.csv" file to a dataframe named "AssnDE107":  Here I am replacing the empty cell values with NA for data cleaning purpose.

``` r
library(ggplot2)
AssnDE107 <- read.csv("HFS Service Data.csv", na.strings = "")
```  

1. **One scatter plot with three variables, properly labeled; choose your representation of the third variable based on what’s best for representing the data.**  
* Three variables are:
  * age  
  * program_unit_description  
  * Adding a third variable in geom point using colour=program_name 
```r
ggplot(data = AssnDE107, aes(x =age , y =program_unit_description , colour=program_name)) +
geom_point(size = 3)
```
