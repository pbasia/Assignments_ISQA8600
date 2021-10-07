Data Exploration Assignment for Heartland Family Service's Data
=
### - Piyush Basia 
  
* Initializing the ggplot2 library in R-studio and loading the data from "HFS Service Data.csv" file to a dataframe named "AssnDE107":  Here I am replacing the empty cell values with NA for data cleaning purpose.

``` r
library(ggplot2)
AssnDE107 <- read.csv("HFS Service Data.csv", na.strings = "")
```
  
* To Understand the data columns, count of their unique values in each column and count of NA values for each variable, I have used the below codes:
```r
rapply(AssnDE107,function(x)length(unique(x)))
```
    ##                   gender             program_name             program_type 
    ##                        4                        3                        1 
    ##                 facility                job_title               staff_name 
    ##                       25                       21                       79 
    ##              actual_date                 duration               event_name 
    ##                     1865                      100                       70 
    ##            activity_type           encounter_with       is_client_involved 
    ##                       11                       13                        2 
    ##                is_noshow                is_locked                is_billed 
    ##                        2                        2                        2 
    ##                  is_paid             date_entered        user_entered_name 
    ##                        1                     1869                       77 
    ##            approved_date      approved_staff_name                submitted 
    ##                     1801                       62                        3 
    ##              is_approved           is_notapproved      is_notapproved_subm 
    ##                        2                        2                        2 
    ## program_unit_description                  sc_code             duration_num 
    ##                       15                       15                       99 
    ##              do_not_bill               do_not_pay         general_location 
    ##                        2                        1                       14 
    ##         program_modifier    program_modifier_code          NormalWorkHours 
    ##                       21                       20                        2 
    ##       duration_other_num           duration_other          travel_time_num 
    ##                       54                       54                        1 
    ##              travel_time        planning_time_num            planning_time 
    ##                        1                        1                        1 
    ##       total_duration_num           total_duration       reason_for_no_show 
    ##                       96                       96                        4 
    ##              is_billable                      zip                    state 
    ##                        1                       10                        5 
    ##                      age                 recordID              simple_race 
    ##                       69                      490                       15 
    ##          ethnic_identity          gender_identity       sexual_orientation 
    ##                        5                        9                       10

``` r
sapply(AssnDE107, function(x) sum(is.na(x)))
```
    ##                   gender             program_name             program_type 
    ##                        0                        0                        0 
    ##                 facility                job_title               staff_name 
    ##                        0                        0                        0 
    ##              actual_date                 duration               event_name 
    ##                        0                       28                        0 
    ##            activity_type           encounter_with       is_client_involved 
    ##                     8069                     7996                        0 
    ##                is_noshow                is_locked                is_billed 
    ##                        0                        0                        0 
    ##                  is_paid             date_entered        user_entered_name 
    ##                        0                        0                      234 
    ##            approved_date      approved_staff_name                submitted 
    ##                        0                      584                      409 
    ##              is_approved           is_notapproved      is_notapproved_subm 
    ##                        0                        0                        0 
    ## program_unit_description                  sc_code             duration_num 
    ##                       46                       46                        0 
    ##              do_not_bill               do_not_pay         general_location 
    ##                        0                        0                      986 
    ##         program_modifier    program_modifier_code          NormalWorkHours 
    ##                      190                      190                        0 
    ##       duration_other_num           duration_other          travel_time_num 
    ##                        0                        0                        0 
    ##              travel_time        planning_time_num            planning_time 
    ##                        0                        0                        0 
    ##       total_duration_num           total_duration       reason_for_no_show 
    ##                        0                        0                     8263 
    ##              is_billable                      zip                    state 
    ##                        0                        0                        0 
    ##                      age                 recordID              simple_race 
    ##                        0                        0                        0 
    ##          ethnic_identity          gender_identity       sexual_orientation 
    ##                        0                        0                        0

<br> </br>
1. **One scatter plot with three variables, properly labeled; choose your representation of the third variable based on what’s best for representing the data.**  
* Three used variables are:
  * age  
  * program_unit_description  
  * Adding a third variable in geom point using colour=program_name 
```r
ggplot(data = AssnDE107, aes(x =age , y =program_unit_description , colour=program_name)) +geom_point(size = 3)+
     labs(title = "Scatter plot with three variables", y = "Unit Description of the Program", x = "Age")
```
| ![Scatter Plot](https://github.com/pbasia/Assignments_ISQA8600/blob/main/Data%20Exploration/1scatter3var.png)<!-- -->
| -
The above scatter plot is composed of three variables: age, program_unit description and program_name. from this plot , we can say that people have mostly participated in the mental health program. The second major program is for the substance use program. The plot also describes that clients between Age 15 to 55 are most likely  to be treated in the programs.

<br> </br>2. **One faceted plot of two variables, properly labeled.**  
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
We have divided the plot using the ethnic_identity of the clients. This plot uses two variables Age and Program Name. We can say from the plot that due to uncollected data or unknown/missing values there are more separations in the plot. However , with the data in hand, the created plot shows the differences of programs being served to the different aged groups accross various ethnicity.

<br> </br>3. **One bar chart, properly labeled.**  
* Used variable is:
  * age    
```r
ggplot(data = AssnDE107)+
    geom_bar(mapping = aes(x=age),colour="white",fill="blue")+
    labs(title = "One bar chart of Age", y = "Count of Clients of this Age", x = "Age of client")
```
| ![Bar Chart](https://github.com/pbasia/Assignments_ISQA8600/blob/main/Data%20Exploration/3BarChart.png)<!-- -->
| -
This Bar chart is composed of only the Age of the Clients of the HFS. It shows how many clients are in which age group. The charts shows that most clients of HFS are Teens and persons in their mid 30's. Also we can observe that there is a drop in the chart for people in their early 20's and avove 45's.
