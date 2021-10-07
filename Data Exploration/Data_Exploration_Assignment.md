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
ggplot(data = AssnDE107, aes(x =age , y =program_unit_description , colour=program_name)) +geom_point(size = 3)+
     labs(title = "Scatter plot with three variables", y = "Unit Description of the Program", x = "Age")
```
| ![Scatter Plot](https://github.com/pbasia/Assignments_ISQA8600/blob/main/Data%20Exploration/1scatter3var.png)<!-- -->
| -

2. **One faceted plot of two variables, properly labeled.**  
* Two used variables are:
  * age  
  * program_name   
```r
ggplot(data = AssnDE107, aes(program_name,age)) +
 geom_line(color = "steelblue", size = 1) +
  geom_point(color = "steelblue") +
   labs(title = "Faceted plot of two variables Age vs Program Name", y = "Age", x = "Name of Program") +
    facet_wrap(.~ethnic_identity)
```
| ![Faceted Plot](https://github.com/pbasia/Assignments_ISQA8600/blob/main/Data%20Exploration/2FacetedPlot.png)<!-- -->
| -

3. **One bar chart, properly labeled.**  
* Used variable is:
  * age    
```r
ggplot(data = AssnDE107)+
    geom_bar(mapping = aes(x=age),colour="white",fill="blue")+
    labs(title = "One bar chart of Age", y = "Count of Clients of this Age", x = "Age of client")
```
| ![Bar Chart](https://github.com/pbasia/Assignments_ISQA8600/blob/main/Data%20Exploration/3BarChart.png)<!-- -->
| -
