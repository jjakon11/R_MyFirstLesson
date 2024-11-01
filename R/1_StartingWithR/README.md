# 1. What is R?

<img src="Attachment/R.png" width="500"/>

-   R is a programming language and software environment for statistical
    analysis, graphics representation and reporting.
-   R Development Core Team:
    -   **R**oss Ihaka and **R**obert Gentleman
        -   That is the reason why this program call **R**
        -   Develop from language S
        -   University of Auckland, New Zealand
    -   What special?
        -   R is freely available under the GNU General Public License
        -   pre-compiled binary versions are provided for various
            operating systems
            -   Linux, Windows and Mac

# 2. Rstudio

<img src="Attachment/RStudio.png" width="500"/>

-   Rsudio is an integrated development environment for R
-   free and open source software
-   Provides a great way to use the R programming language and interact
    with other software components.
-   Interface of Rstudio
    -   Top right panel:
        -   **Environment**: all variables, datasets, and functions
            stored are shown;
        -   **History:** a summary of the actions taken in the session
        -   **Connections:** to connectwith other data sources
    -   Bottom right panel:
        -   **Files:** choose the working directory
        -   **Plots:** show the graphics generated
        -   **Packages:** libraries loaded are shown
        -   **Help:** get assistance with functions and commands
        -   **Viewer:** have a look at data structures
    -   Bottom left panel:
        -   Console
        -   Terminal
    -   Top left:
        -   file window: we write our code programs and able to save it
            for further use.
            -   **Script**: it is a .R file, a blank notebook
            -   **R Markdown**: .Rmd file
                -   Code is inserted in blocks called *chunks*.
                -   Good to output: Allows to produce an HTML, PDF or
                    Microsoft word report where text, code and outputs
                    are shown at once in a pretty and understandable
                    format.

# 3. Basic frame work in R language

-   Package

-   Function

-   Argument

## 3.1.Package

-   R packages are extensions to the R statistical programming language.
-   Use library() to call out the package.
-   One package will contain numerous of **function** to proceed the
    specific progress.
    -   ggplot2 package: for data visualization
    -   tidyverse package: for tidy the data
    -   dplyr package: another package for tidy the data
-   CRAN (Comprehensive R Archive Network): the main repository for R
    packages
    -   The main advantage to getting your package on CRAN is that it
        will be easier for users to install.
    -   base package
    -   contributed package
-   Having a package to do something:
    1.  Install the package: install.packages(““)
    2.  Call your package out: library()

``` r
install.packages("vegan")
library(vegan)
```

## 3.2.Function

-   Function is an object, a collection of instructions that perform
    specific operation

``` r
  x.vec <- c(1:5)
  x.vec

  mean(x.vec)
  var(x.vec)
  log(x.vec)
```

## 3.3.Argument

-   A function usually requires input at least one argument or
    statistical formulas or model.

-   Argument can be a numerical value, text, data frame or any object in
    R language.

    -   Required argument
    -   Optional argument
    -   ellipsis argument

``` r
lm(Sepal.Length~Petal.Length, data=iris)
```

    ## 
    ## Call:
    ## lm(formula = Sepal.Length ~ Petal.Length, data = iris)
    ## 
    ## Coefficients:
    ##  (Intercept)  Petal.Length  
    ##       4.3066        0.4089

``` r
model <- lm(Sepal.Length~Petal.Length, data=iris)
summary(aov(model))
```

    ##               Df Sum Sq Mean Sq F value Pr(>F)    
    ## Petal.Length   1  77.64   77.64   468.6 <2e-16 ***
    ## Residuals    148  24.53    0.17                   
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

# 4. Data strucutres

## 4.1. Variables and Basic Arithmetic

-   Use R as a normal calculator

``` r
3
3+4
3-5
2*6
5/3
15%%2
15%/%2
```

-   Define variables

``` r
x <- 4
x
```

    ## [1] 4

``` r
y <- 5

z <- x+y
z
```

    ## [1] 9

## 4.2. Basic data types

we can use class() to check what knid of variable is being used.

### 4.2.1. Numeric

``` r
number <- 4.3
class(number)
```

    ## [1] "numeric"

``` r
2.73e4
```

    ## [1] 27300

``` r
1/2.73e4
```

    ## [1] 3.663004e-05

### 4.2.2. Character:

to introduce characters, we need to use quatation marks.

``` r
world <-"Hello World"
class(world)
```

    ## [1] "character"

### 4.3.3. Logical

logical class encodes Boolean values-\> TRUE and FALSE

``` r
yes.no <- TRUE
class(yes.no)
```

    ## [1] "logical"

### 4.3.4. special data type: NULL and NA

-   **Null** means an empty object: contain no information

-   **NA** means a non-available entry and representing a missing value
    in data analysis: contain information.

## 4.3. Vectors

A vector is an array of elements.We can create vectors in R with the
command **c()** and the elements inside separated by commas

``` r
#Numeric
VN <- c(1,2,3,4)
VN
```

    ## [1] 1 2 3 4

``` r
length(VN)
```

    ## [1] 4

``` r
#Character
VC <- c("Monday", "Tuesday", "Wednesday")
VC
```

    ## [1] "Monday"    "Tuesday"   "Wednesday"

``` r
#Logical
VL <- c(TRUE, FALSE)
VL
```

    ## [1]  TRUE FALSE

The command c() comes from combination, and it is used to combine
elements that must be of homogeneous class.

-   If the data type is not the same…

    -   The information will coerced into the same class

    -   The hierarchy will be: Character \> Numeric \> Logical

``` r
Example1 <- c(3.4, "Goodjob")
class(Example1)
```

    ## [1] "character"

``` r
Example2 <- c(TRUE, 3.4)
class(Example2)
```

    ## [1] "numeric"

``` r
Example3 <- c(NA, 3, 4)
class(Example3)
```

    ## [1] "numeric"

### More information of numeric vectors

#### 4.3.1. Produce a consecutive numbers

``` r
c(0,1,2,3,4,5,6,7,8,9,10)
```

    ##  [1]  0  1  2  3  4  5  6  7  8  9 10

``` r
0:10
```

    ##  [1]  0  1  2  3  4  5  6  7  8  9 10

``` r
0:100
```

    ##   [1]   0   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17
    ##  [19]  18  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35
    ##  [37]  36  37  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53
    ##  [55]  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69  70  71
    ##  [73]  72  73  74  75  76  77  78  79  80  81  82  83  84  85  86  87  88  89
    ##  [91]  90  91  92  93  94  95  96  97  98  99 100

``` r
c(0:100)
```

    ##   [1]   0   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17
    ##  [19]  18  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35
    ##  [37]  36  37  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53
    ##  [55]  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69  70  71
    ##  [73]  72  73  74  75  76  77  78  79  80  81  82  83  84  85  86  87  88  89
    ##  [91]  90  91  92  93  94  95  96  97  98  99 100

``` r
seq(0,100, by=1)
```

    ##   [1]   0   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17
    ##  [19]  18  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35
    ##  [37]  36  37  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53
    ##  [55]  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69  70  71
    ##  [73]  72  73  74  75  76  77  78  79  80  81  82  83  84  85  86  87  88  89
    ##  [91]  90  91  92  93  94  95  96  97  98  99 100

``` r
seq(0,100, by=25)
```

    ## [1]   0  25  50  75 100

``` r
# if we want to repeat a number or a group of number

rep(c(3, 2,1), time=10)
```

    ##  [1] 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1 3 2 1

``` r
rep(c("Happy", "Angry", "Sad"), time=5)
```

    ##  [1] "Happy" "Angry" "Sad"   "Happy" "Angry" "Sad"   "Happy" "Angry" "Sad"  
    ## [10] "Happy" "Angry" "Sad"   "Happy" "Angry" "Sad"

``` r
rep(c(TRUE, FALSE), time=3)
```

    ## [1]  TRUE FALSE  TRUE FALSE  TRUE FALSE

``` r
rep(c(3,2,1), each=10)
```

    ##  [1] 3 3 3 3 3 3 3 3 3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1

``` r
rep(c(3,2,1), times=c(2,1,3))
```

    ## [1] 3 3 2 1 1 1

#### 4.3.2. Label the names to the numeric vector

``` r
temperature <- c(28, 29, 27,27,30)
names(temperature)
```

    ## NULL

``` r
names(temperature) <-c("Monday", "Tuesday", "Wednesday","Thursday", "Friday")


rains <- c(0, 5, 6, 0, 2)
names(rains) <-c("Monday", "Tuesday", "Wednesday","Thursday", "Friday")
rains
```

    ##    Monday   Tuesday Wednesday  Thursday    Friday 
    ##         0         5         6         0         2

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
total.rains <- sum(rains)
```

If you are going to select the element in vector -\> use “brackets” **\[
\]** - Bracket are used for indexing into a vector, matrix, array, list
and dataframe. - Also called *extraction operators*, extract specific
elements from a vector or matrix

``` r
rains[2]
```

    ## Tuesday 
    ##       5

``` r
rains[c(1,2)]
```

    ##  Monday Tuesday 
    ##       0       5

``` r
temperature[c(2,3,4)]
```

    ##   Tuesday Wednesday  Thursday 
    ##        29        27        27

``` r
temperature[2:4]
```

    ##   Tuesday Wednesday  Thursday 
    ##        29        27        27

``` r
temperature["Wednesday"]
```

    ## Wednesday 
    ##        27

#### 4.3.3. Logical vector

``` r
rains>0
```

    ##    Monday   Tuesday Wednesday  Thursday    Friday 
    ##     FALSE      TRUE      TRUE     FALSE      TRUE

``` r
temperature>=29
```

    ##    Monday   Tuesday Wednesday  Thursday    Friday 
    ##     FALSE      TRUE     FALSE     FALSE      TRUE

``` r
# to select day whether the temperature is larger than 29 degree in rain vector
rains[temperature>=29]
```

    ## Tuesday  Friday 
    ##       5       2

``` r
# all(), checking whether the conditions are statisfied by all elements of the vector.
all(temperature>=29)
```

    ## [1] FALSE

``` r
# any(),  checking whether the condition is satisfied by, at least, one element of the vector.
any(temperature>=29)
```

    ## [1] TRUE

``` r
# which(), find the actual positions of those elements satisfying the condition and return the TRUE ones as a vector.
which(temperature>=29)
```

    ## Tuesday  Friday 
    ##       2       5

#### 4.3.4. Order and sort the vector

``` r
order(temperature)
```

    ## [1] 3 4 1 2 5

``` r
temperature[order(temperature)]
```

    ## Wednesday  Thursday    Monday   Tuesday    Friday 
    ##        27        27        28        29        30

``` r
# calculation
sum(temperature)
```

    ## [1] 141

``` r
mean(temperature)
```

    ## [1] 28.2

``` r
sd(temperature)
```

    ## [1] 1.30384

``` r
max(temperature)
```

    ## [1] 30

``` r
min(temperature)
```

    ## [1] 27

``` r
range(temperature)
```

    ## [1] 27 30

``` r
quantile(temperature)
```

    ##   0%  25%  50%  75% 100% 
    ##   27   27   28   29   30

``` r
quantile(temperature, 0.05)
```

    ## 5% 
    ## 27

# Next Week

-   Matrix
-   Factors
-   Data Frames
-   Lists

------------------------------------------------------------------------

# Excercise

-   Please build two separate vectors for temperature and precipitation,
    each labeled with the name of the day of the week (Sunday to
    Saturday).

    -   *Ensure that the data is referenced from the Taichung weather
        station*
    -   *Please refer to the data last week*

    1.  What were the average, maximum, and minimum temperatures in
        Taichung last week?

    2.  What was the total precipitation in Taichung last week?

    3.  How many days did precipitation exceed 30mm in a day?
