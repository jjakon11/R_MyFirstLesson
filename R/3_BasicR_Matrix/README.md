# **Class 3:Basic R Matrix**

# 1. Data Structrue

In class2, we have been describe about basic data types and vector.
Here, we extand the concept from vector, introducing Matrix and Factors

## 1.1. Matrix

Matrix are one of the most important tools in mathematics, used to
encode a 2-dimensional array of numbers, each of them named by their row
and column coordinates. And the idea of mathematics are the same as the
programming.

**matrix()** is a function that allows to create a matrix.

``` r
matrix(data=NA, nrow=1, ncol=1, byrow=FALSE, dimnames = NULL)
```

*data* is the vector of data we want to include in the matrix *nrow* is
the number of rows *ncol* is the number of columns *byrow* indicates
whether we fill the matrix with the data vector by rows or columns; by
default it is filled by columns *dimnames* allows to include a list of 2
elements containing names for rows and columns; there are no names by
default.

``` r
matrix(1:9, byrow = TRUE, nrow=3)
matrix(1:9, byrow = FALSE, nrow=3)

matrix(1:15, nrow=2)

matrix(c("J", "F", "M", "A", "M", "J"), ncol=3, byrow=TRUE)
```

Create a weather matrix. We can combine “temperature” and “rains” vector
with matrix() to create a new matrix. And then, we can give the
particlar names to each row and column with **rownames()** and
**colnames()**.

First, we had the vector from Class2

``` r
temperature <- c(28, 29, 27,27,30)
temperature
```

    ## [1] 28 29 27 27 30

``` r
#names(temperature)
names(temperature) <-c("Monday", "Tuesday", "Wednesday","Thursday", "Friday")
temperature
```

    ##    Monday   Tuesday Wednesday  Thursday    Friday 
    ##        28        29        27        27        30

``` r
temperature+273.15
```

    ##    Monday   Tuesday Wednesday  Thursday    Friday 
    ##    301.15    302.15    300.15    300.15    303.15

``` r
temperature*1.8+32
```

    ##    Monday   Tuesday Wednesday  Thursday    Friday 
    ##      82.4      84.2      80.6      80.6      86.0

``` r
rains <- c(0, 5, 6, 0, 2)
names(rains) <-c("Monday", "Tuesday", "Wednesday","Thursday", "Friday")
rains
```

    ##    Monday   Tuesday Wednesday  Thursday    Friday 
    ##         0         5         6         0         2

Then, matrix the *temperatrue* and *rain* vector together

``` r
climate <- matrix(c(temperature, rains), byrow=TRUE, nrow=2)
rownames(climate) <- c("Temperature", "Rains")
colnames(climate)<-c("Monday", "Tuesday", "Wednesday","Thursday", "Friday")
climate
```

Matrix have 2 dimension, by using **dim()**, we can understand the
number of columns and rows.

``` r
dim(climate)
```

    ## [1] 2 5

Add a new data as a row, **rbind()**. rbind is the meaning of
**bind**ing two matrix or data by **r**ow

``` r
#Add a new data as a row, rbind()
Winds <- c(30, 25, 22, 24, 18)
climate1 <- rbind(climate, Winds); climate1
```

    ##             Monday Tuesday Wednesday Thursday Friday
    ## Temperature     28      29        27       27     30
    ## Rains            0       5         6        0      2
    ## Winds           30      25        22       24     18

Add the data with another column, use **cbind()**. cbind is the meaning
of **bind**ing two matrix or data by **c**olumn.

``` r
Saturday <- c(26, 0, 20)
climate2 <- cbind(climate1,Saturday ); climate2
```

    ##             Monday Tuesday Wednesday Thursday Friday Saturday
    ## Temperature     28      29        27       27     30       26
    ## Rains            0       5         6        0      2        0
    ## Winds           30      25        22       24     18       20

Selecting the matrix is similar to vectors. However, instead of one
coordinate, now we have two dimension of them. The first referring to
the row. The second referring to the column. \[**row**,**column**\]

``` r
climate2[2,3]

climate2[, 4]

climate2[1, ]

climate2[, "Friday"]

climate2["Rains", ]
```

calculation to the matrix

``` r
mean(climate2[1, ])

climate2*3

climate2^2

climate2*climate2

climate2*c(0.5,1,2)

climate2*climate2[1,]
```

## 1.2. Factors

``` r
# Numeric
things <- c(1,2,3,4,5)
as.factor(things)
```

    ## [1] 1 2 3 4 5
    ## Levels: 1 2 3 4 5

``` r
#character
sizes <- c("Small", "Big", "Big", "Medium", "Medium", "Small",
           "Medium", "Small", "Small")
sizes
```

    ## [1] "Small"  "Big"    "Big"    "Medium" "Medium" "Small"  "Medium" "Small" 
    ## [9] "Small"

``` r
summary(sizes)
```

    ##    Length     Class      Mode 
    ##         9 character character

``` r
sizes.f <- factor(sizes)

sizes.f
```

    ## [1] Small  Big    Big    Medium Medium Small  Medium Small  Small 
    ## Levels: Big Medium Small

``` r
summary(sizes.f)
```

    ##    Big Medium  Small 
    ##      2      3      4

``` r
levels(sizes.f)
```

    ## [1] "Big"    "Medium" "Small"

``` r
lo <- c(TRUE, F, T, F, F, F)
as.factor(lo)
```

    ## [1] TRUE  FALSE TRUE  FALSE FALSE FALSE
    ## Levels: FALSE TRUE

# 2. Excercise

1.  Please build two separate vectors for temperature and precipitation,
    each labeled with the name of the day of the week (Sunday to
    Saturday, 9/10-9/16).

    -   *Ensure that the data is referenced from the Taichung weather
        station*
    -   *Please refer to the data last week*

    1.  What were the average, maximum, and minimum temperatures in
        Taichung last week?

    2.  What was the total precipitation in Taichung last week?

    3.  How many days did precipitation exceed 30mm in a day?

2.  Please create a 4 x 7 matrix with temperature, precipitation, wind
    speed and wind direction as the row name and Monday to Sunday as the
    column name.
