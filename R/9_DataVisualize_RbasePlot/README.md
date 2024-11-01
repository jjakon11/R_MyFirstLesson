# **Class 9: Data Visualize, Rbase Plot**

# Why we need to plot something out?

<img src="https://github.com/jjakon11/30DayMapChallenge/blob/main/2023_Challenge/Map/Day2_Lines.png" width="500"/>

<img src="https://github.com/jjakon11/30DayMapChallenge/blob/main/2024_Challenge/Map/Day1_Points.png" width="500"/>

Visualization is a powerful way to convey the ideas and findings of your
research or to present data effectively.

1.  Clarity

2.  Engagement

3.  Patterns and trends

4.  Memory retention

5.  Storytelling

6.  Comparison

# 1. Basic plot

## 1.1 Read data

``` r
Excerdt3 <- read.csv("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/9_DataVisualize_RbasePlot/Attachment/Excerdt3.csv")
```

## 1.2 Histogram

``` r
hist(Excerdt3$Precip_value)
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-2-1.png" width="80%" />

``` r
hist(Excerdt3$Precip_value, main="Precipitation frequency")
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-2-2.png" width="80%" />

``` r
#You can't do the things like this
#hist(Precip_value, main ="Precipitation frequency" ,data= Complex_long)
```

## 1.3 Scatter plot

``` r
plot( x=Excerdt3$Z,y=Excerdt3$averageT_value)
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-3-1.png" width="80%" />

``` r
#give some color
plot(Excerdt3$Precip_value,Excerdt3$averageT_value, col = Excerdt3$station)
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-3-2.png" width="80%" />

``` r
#change the type of point
plot(Excerdt3$Precip_value,Excerdt3$averageT_value, col = Excerdt3$station, pch=3)
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-3-3.png" width="80%" />

Here are different types of the point, change the types of the point
with the numbers.

<img src="Attachment/PCH.jpg" width="500"/>

``` r
plot(Excerdt3$Precip_value,Excerdt3$averageT_value, col = Excerdt3$station, pch=20)
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-4-1.png" width="80%" />

``` r
#cex -> control size
plot(Excerdt3$Precip_value,Excerdt3$averageT_value, 
     col = Excerdt3$station, pch=19 ,cex=0.5) 
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-4-2.png" width="80%" />

``` r
#give it a title
plot(Excerdt3$Precip_value,Excerdt3$averageT_value, 
     col = Excerdt3$station, pch=19 ,cex=3, main="This is a title") 
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-4-3.png" width="80%" />

``` r
plot(Excerdt3$Precip_value,Excerdt3$averageT_value, 
     col = Excerdt3$station, pch=19 ,cex=3, main="This is a title", 
     xlab="Precipitation (mm)", ylab="Average temperature (C)") 
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-4-4.png" width="80%" />

## 1.4 Boxplot

``` r
boxplot(Excerdt3$Precip_value~Excerdt3$station)
```

<img src="9_DataVisualize_RbasePlot_files/figure-markdown_github/unnamed-chunk-5-1.png" width="80%" />

## 1.5 save your plot

``` r
png("Excercise_output/rplot.png", width = 5000, height = 5000,res=1000)
plot(Excerdt3$Precip_value,Excerdt3$averageT_value, 
     col = Excerdt3$station, pch=19 ,cex=3, main="This is a title", 
     xlab="Precipitation (mm)", ylab="Average temperature (C)") 
dev.off()
```

    ## png 
    ##   2
