## Worst Plots Contest
================

## R Markdown

``` r
newdata <- read.csv("HFS Service Data.csv", na.strings = "")
```

``` r
library(ggplot2)
ggplot(newdata, aes(x =program_name , y=duration, color=program_name))+stat_summary(fun = "mean", geom = "bar")
```

![](https://github.com/pbasia/Assignments_ISQA8600/blob/main/Worst%20Plots/images/unnamed-chunk-2-1.png)<!-- -->
