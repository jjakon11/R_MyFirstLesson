# **Class 4:Basic R Read Data**

# 1. Matrix

``` r
temperature <- c(28, 29, 27,27,30)
rains <- c(0, 5, 6, 0, 2)
Winds <- c(30, 25, 22, 24, 18)

climate <- matrix(c(temperature, rains, Winds), byrow=TRUE, nrow=3)
rownames(climate) <- c("Temperature", "Rains", "Winds")
colnames(climate)<-c("Monday", "Tuesday", "Wednesday","Thursday", "Friday")
climate
```

    ##             Monday Tuesday Wednesday Thursday Friday
    ## Temperature     28      29        27       27     30
    ## Rains            0       5         6        0      2
    ## Winds           30      25        22       24     18

``` r
class(climate)
```

    ## [1] "matrix" "array"

# 2. Data frame

## 2.1 Create the Data

``` r
climatedt <- data.frame(climate)
class(climatedt)
```

    ## [1] "data.frame"

``` r
climatedt
```

    ##             Monday Tuesday Wednesday Thursday Friday
    ## Temperature     28      29        27       27     30
    ## Rains            0       5         6        0      2
    ## Winds           30      25        22       24     18

Create the another dataframe by vector

``` r
x <- 10:1
y <- -4:5
sp <- c("A", "B","C","D", "E", 
        "F", "G", "H", "I", "J")
abundance <- c(sample(50:1000, 10, replace=F))

DF <- data.frame(x, y, sp, abundance)
class(DF)
```

    ## [1] "data.frame"

``` r
str(DF)
```

    ## 'data.frame':    10 obs. of  4 variables:
    ##  $ x        : int  10 9 8 7 6 5 4 3 2 1
    ##  $ y        : int  -4 -3 -2 -1 0 1 2 3 4 5
    ##  $ sp       : chr  "A" "B" "C" "D" ...
    ##  $ abundance: int  515 913 197 931 495 93 367 736 345 402

``` r
View(DF)

head(DF)
```

    ##    x  y sp abundance
    ## 1 10 -4  A       515
    ## 2  9 -3  B       913
    ## 3  8 -2  C       197
    ## 4  7 -1  D       931
    ## 5  6  0  E       495
    ## 6  5  1  F        93

``` r
head(DF, 3)
```

    ##    x  y sp abundance
    ## 1 10 -4  A       515
    ## 2  9 -3  B       913
    ## 3  8 -2  C       197

``` r
nrow(DF)
```

    ## [1] 10

``` r
ncol(DF)
```

    ## [1] 4

``` r
dim(DF)
```

    ## [1] 10  4

``` r
colnames(DF)
```

    ## [1] "x"         "y"         "sp"        "abundance"

``` r
colnames(DF)[3]
```

    ## [1] "sp"

``` r
rownames(DF)
```

    ##  [1] "1"  "2"  "3"  "4"  "5"  "6"  "7"  "8"  "9"  "10"

``` r
DF$sp
```

    ##  [1] "A" "B" "C" "D" "E" "F" "G" "H" "I" "J"

``` r
class(DF$sp)
```

    ## [1] "character"

``` r
DF$sp <- factor(DF$sp)
class(DF$sp)
```

    ## [1] "factor"

``` r
str(DF)
```

    ## 'data.frame':    10 obs. of  4 variables:
    ##  $ x        : int  10 9 8 7 6 5 4 3 2 1
    ##  $ y        : int  -4 -3 -2 -1 0 1 2 3 4 5
    ##  $ sp       : Factor w/ 10 levels "A","B","C","D",..: 1 2 3 4 5 6 7 8 9 10
    ##  $ abundance: int  515 913 197 931 495 93 367 736 345 402

The difference between data frame and matrix is that matrix can only
contain a single class of data, while data frames can consist of many
different class of data.

## 2.2 Get the example data from package

``` r
data(iris)
iris
```

    ##     Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
    ## 1            5.1         3.5          1.4         0.2     setosa
    ## 2            4.9         3.0          1.4         0.2     setosa
    ## 3            4.7         3.2          1.3         0.2     setosa
    ## 4            4.6         3.1          1.5         0.2     setosa
    ## 5            5.0         3.6          1.4         0.2     setosa
    ## 6            5.4         3.9          1.7         0.4     setosa
    ## 7            4.6         3.4          1.4         0.3     setosa
    ## 8            5.0         3.4          1.5         0.2     setosa
    ## 9            4.4         2.9          1.4         0.2     setosa
    ## 10           4.9         3.1          1.5         0.1     setosa
    ## 11           5.4         3.7          1.5         0.2     setosa
    ## 12           4.8         3.4          1.6         0.2     setosa
    ## 13           4.8         3.0          1.4         0.1     setosa
    ## 14           4.3         3.0          1.1         0.1     setosa
    ## 15           5.8         4.0          1.2         0.2     setosa
    ## 16           5.7         4.4          1.5         0.4     setosa
    ## 17           5.4         3.9          1.3         0.4     setosa
    ## 18           5.1         3.5          1.4         0.3     setosa
    ## 19           5.7         3.8          1.7         0.3     setosa
    ## 20           5.1         3.8          1.5         0.3     setosa
    ## 21           5.4         3.4          1.7         0.2     setosa
    ## 22           5.1         3.7          1.5         0.4     setosa
    ## 23           4.6         3.6          1.0         0.2     setosa
    ## 24           5.1         3.3          1.7         0.5     setosa
    ## 25           4.8         3.4          1.9         0.2     setosa
    ## 26           5.0         3.0          1.6         0.2     setosa
    ## 27           5.0         3.4          1.6         0.4     setosa
    ## 28           5.2         3.5          1.5         0.2     setosa
    ## 29           5.2         3.4          1.4         0.2     setosa
    ## 30           4.7         3.2          1.6         0.2     setosa
    ## 31           4.8         3.1          1.6         0.2     setosa
    ## 32           5.4         3.4          1.5         0.4     setosa
    ## 33           5.2         4.1          1.5         0.1     setosa
    ## 34           5.5         4.2          1.4         0.2     setosa
    ## 35           4.9         3.1          1.5         0.2     setosa
    ## 36           5.0         3.2          1.2         0.2     setosa
    ## 37           5.5         3.5          1.3         0.2     setosa
    ## 38           4.9         3.6          1.4         0.1     setosa
    ## 39           4.4         3.0          1.3         0.2     setosa
    ## 40           5.1         3.4          1.5         0.2     setosa
    ## 41           5.0         3.5          1.3         0.3     setosa
    ## 42           4.5         2.3          1.3         0.3     setosa
    ## 43           4.4         3.2          1.3         0.2     setosa
    ## 44           5.0         3.5          1.6         0.6     setosa
    ## 45           5.1         3.8          1.9         0.4     setosa
    ## 46           4.8         3.0          1.4         0.3     setosa
    ## 47           5.1         3.8          1.6         0.2     setosa
    ## 48           4.6         3.2          1.4         0.2     setosa
    ## 49           5.3         3.7          1.5         0.2     setosa
    ## 50           5.0         3.3          1.4         0.2     setosa
    ## 51           7.0         3.2          4.7         1.4 versicolor
    ## 52           6.4         3.2          4.5         1.5 versicolor
    ## 53           6.9         3.1          4.9         1.5 versicolor
    ## 54           5.5         2.3          4.0         1.3 versicolor
    ## 55           6.5         2.8          4.6         1.5 versicolor
    ## 56           5.7         2.8          4.5         1.3 versicolor
    ## 57           6.3         3.3          4.7         1.6 versicolor
    ## 58           4.9         2.4          3.3         1.0 versicolor
    ## 59           6.6         2.9          4.6         1.3 versicolor
    ## 60           5.2         2.7          3.9         1.4 versicolor
    ## 61           5.0         2.0          3.5         1.0 versicolor
    ## 62           5.9         3.0          4.2         1.5 versicolor
    ## 63           6.0         2.2          4.0         1.0 versicolor
    ## 64           6.1         2.9          4.7         1.4 versicolor
    ## 65           5.6         2.9          3.6         1.3 versicolor
    ## 66           6.7         3.1          4.4         1.4 versicolor
    ## 67           5.6         3.0          4.5         1.5 versicolor
    ## 68           5.8         2.7          4.1         1.0 versicolor
    ## 69           6.2         2.2          4.5         1.5 versicolor
    ## 70           5.6         2.5          3.9         1.1 versicolor
    ## 71           5.9         3.2          4.8         1.8 versicolor
    ## 72           6.1         2.8          4.0         1.3 versicolor
    ## 73           6.3         2.5          4.9         1.5 versicolor
    ## 74           6.1         2.8          4.7         1.2 versicolor
    ## 75           6.4         2.9          4.3         1.3 versicolor
    ## 76           6.6         3.0          4.4         1.4 versicolor
    ## 77           6.8         2.8          4.8         1.4 versicolor
    ## 78           6.7         3.0          5.0         1.7 versicolor
    ## 79           6.0         2.9          4.5         1.5 versicolor
    ## 80           5.7         2.6          3.5         1.0 versicolor
    ## 81           5.5         2.4          3.8         1.1 versicolor
    ## 82           5.5         2.4          3.7         1.0 versicolor
    ## 83           5.8         2.7          3.9         1.2 versicolor
    ## 84           6.0         2.7          5.1         1.6 versicolor
    ## 85           5.4         3.0          4.5         1.5 versicolor
    ## 86           6.0         3.4          4.5         1.6 versicolor
    ## 87           6.7         3.1          4.7         1.5 versicolor
    ## 88           6.3         2.3          4.4         1.3 versicolor
    ## 89           5.6         3.0          4.1         1.3 versicolor
    ## 90           5.5         2.5          4.0         1.3 versicolor
    ## 91           5.5         2.6          4.4         1.2 versicolor
    ## 92           6.1         3.0          4.6         1.4 versicolor
    ## 93           5.8         2.6          4.0         1.2 versicolor
    ## 94           5.0         2.3          3.3         1.0 versicolor
    ## 95           5.6         2.7          4.2         1.3 versicolor
    ## 96           5.7         3.0          4.2         1.2 versicolor
    ## 97           5.7         2.9          4.2         1.3 versicolor
    ## 98           6.2         2.9          4.3         1.3 versicolor
    ## 99           5.1         2.5          3.0         1.1 versicolor
    ## 100          5.7         2.8          4.1         1.3 versicolor
    ## 101          6.3         3.3          6.0         2.5  virginica
    ## 102          5.8         2.7          5.1         1.9  virginica
    ## 103          7.1         3.0          5.9         2.1  virginica
    ## 104          6.3         2.9          5.6         1.8  virginica
    ## 105          6.5         3.0          5.8         2.2  virginica
    ## 106          7.6         3.0          6.6         2.1  virginica
    ## 107          4.9         2.5          4.5         1.7  virginica
    ## 108          7.3         2.9          6.3         1.8  virginica
    ## 109          6.7         2.5          5.8         1.8  virginica
    ## 110          7.2         3.6          6.1         2.5  virginica
    ## 111          6.5         3.2          5.1         2.0  virginica
    ## 112          6.4         2.7          5.3         1.9  virginica
    ## 113          6.8         3.0          5.5         2.1  virginica
    ## 114          5.7         2.5          5.0         2.0  virginica
    ## 115          5.8         2.8          5.1         2.4  virginica
    ## 116          6.4         3.2          5.3         2.3  virginica
    ## 117          6.5         3.0          5.5         1.8  virginica
    ## 118          7.7         3.8          6.7         2.2  virginica
    ## 119          7.7         2.6          6.9         2.3  virginica
    ## 120          6.0         2.2          5.0         1.5  virginica
    ## 121          6.9         3.2          5.7         2.3  virginica
    ## 122          5.6         2.8          4.9         2.0  virginica
    ## 123          7.7         2.8          6.7         2.0  virginica
    ## 124          6.3         2.7          4.9         1.8  virginica
    ## 125          6.7         3.3          5.7         2.1  virginica
    ## 126          7.2         3.2          6.0         1.8  virginica
    ## 127          6.2         2.8          4.8         1.8  virginica
    ## 128          6.1         3.0          4.9         1.8  virginica
    ## 129          6.4         2.8          5.6         2.1  virginica
    ## 130          7.2         3.0          5.8         1.6  virginica
    ## 131          7.4         2.8          6.1         1.9  virginica
    ## 132          7.9         3.8          6.4         2.0  virginica
    ## 133          6.4         2.8          5.6         2.2  virginica
    ## 134          6.3         2.8          5.1         1.5  virginica
    ## 135          6.1         2.6          5.6         1.4  virginica
    ## 136          7.7         3.0          6.1         2.3  virginica
    ## 137          6.3         3.4          5.6         2.4  virginica
    ## 138          6.4         3.1          5.5         1.8  virginica
    ## 139          6.0         3.0          4.8         1.8  virginica
    ## 140          6.9         3.1          5.4         2.1  virginica
    ## 141          6.7         3.1          5.6         2.4  virginica
    ## 142          6.9         3.1          5.1         2.3  virginica
    ## 143          5.8         2.7          5.1         1.9  virginica
    ## 144          6.8         3.2          5.9         2.3  virginica
    ## 145          6.7         3.3          5.7         2.5  virginica
    ## 146          6.7         3.0          5.2         2.3  virginica
    ## 147          6.3         2.5          5.0         1.9  virginica
    ## 148          6.5         3.0          5.2         2.0  virginica
    ## 149          6.2         3.4          5.4         2.3  virginica
    ## 150          5.9         3.0          5.1         1.8  virginica

``` r
View(iris)

str(iris)
```

    ## 'data.frame':    150 obs. of  5 variables:
    ##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
    ##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
    ##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
    ##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
    ##  $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...

``` r
head(iris)
```

    ##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ## 1          5.1         3.5          1.4         0.2  setosa
    ## 2          4.9         3.0          1.4         0.2  setosa
    ## 3          4.7         3.2          1.3         0.2  setosa
    ## 4          4.6         3.1          1.5         0.2  setosa
    ## 5          5.0         3.6          1.4         0.2  setosa
    ## 6          5.4         3.9          1.7         0.4  setosa

``` r
str(iris)
```

    ## 'data.frame':    150 obs. of  5 variables:
    ##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
    ##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
    ##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
    ##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
    ##  $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...

## 2.3 Input data from your own data

Before input your data input, we need to setup working directory before
we input or out put somethings.

``` r
# Check your own working directory
getwd()

# Set up your own working directory
setwd("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson")


# Different direction of your / and \\
setwd("E:\\Drive\\2_lab\\Edu5_Course\\R_MyFirstLesson")
```

### read csv file

``` r
mydt <- read.csv("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/example.csv")
```

``` r
# Or using file.choose to pop out a window to select the file by your own
mydt2 <- read.csv(file.choose()) #example.csv # It was my favorite, but I don't love it anymore.

#mydt <- read.csv(paste(getwd(), "/example.csv", sep=""))
```

### export the csv file

``` r
write.csv(climatedt, "Excercise_output/climatedt.csv",  row.names = T)
```

*Excercise* –\> Read a file

``` r
Excercise1 <- read.csv("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/Excercise.csv",
    fileEncoding = "utf8")

# Any problem?

Excercise <- read.csv("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/Excercise.csv",
    fileEncoding = "big5")
```

### read txt file

``` r
mydt3 <- read.table("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/Excercise.txt", fileEncoding = "big5", header=T)
```

### read Excel file

``` r
library(readxl) #install.packages("readxl")

mydt4 <- read_xlsx("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/Excercise2.xlsx", sheet=1)

mydt5 <- read_xlsx("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/Excercise2.xlsx", sheet=2)

mydt5 <- read_xlsx("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/Excercise2.xlsx", sheet="spcode")
```

### a comprise Data in R

``` r
save(mydt4, mydt5, iris, file="E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/myiris.rdata")
rm(mydt4, mydt5, iris)

#mydt4 
#mydt5
#DF

load("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/4_BasicR_ReadData/Attachment/myiris.rdata")
```

# 3. Lists

Lists can be conceived as vectors made of elements which can be of
different lengths, sizes, type, etc. It can contain a numerous type of
data, including vectors, matrix and data frames. You can imagine that
List is a room of data, and that contain a numerous type of data in
different layer.

``` r
list(1,2,3)
```

    ## [[1]]
    ## [1] 1
    ## 
    ## [[2]]
    ## [1] 2
    ## 
    ## [[3]]
    ## [1] 3

``` r
list(c(1,2,3))
```

    ## [[1]]
    ## [1] 1 2 3

``` r
list1 <- list(c(1,2,3), 3:7)
list2 <- list(iris, mydt3, temperature)
```

Finally, we finish all of the basic information of R.

## Input your data Now

Please input your own data and see what will happens.

# 4. Excercise

1.  Please create a 4 x 7 matrix with temperature, precipitation, wind
    speed and wind direction as the row name and Monday to Sunday as the
    column name. Then, transfer the matrix into data frame.

2.  Please output the data frame that created by the first question.

jjakon11@gmail.com
