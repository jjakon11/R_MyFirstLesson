# **Class 2:Basic R Data Types**

# 1. Data strucutres

## 1.1. Variables and Basic Arithmetic

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

## 1.2. Basic data types

We can use class() to check what kind of variable is being used.
**class()** is a function that can used to understand the encoding
properties.

### 1.2.1. Numeric

``` r
number <- 4.3
class(number)
```

    ## [1] "numeric"

``` r
integer <- 10
class(integer)
```

    ## [1] "numeric"

``` r
2.73e4 # 2.73*10^4
```

    ## [1] 27300

``` r
1/2.73e4 #-> 3.663004e-05 -> 3.663004 * 10^-5
```

    ## [1] 3.663004e-05

### 1.2.2. Character

To introduce characters, we need to use quotation marks.

``` r
world <-"Hello World"
class(world)
```

    ## [1] "character"

### 1.2.3. Logical

Logical class encodes Boolean values-\> TRUE and FALSE

``` r
yes.no <- TRUE
class(yes.no)
```

    ## [1] "logical"

``` r
is.logical(yes.no)
```

    ## [1] TRUE

``` r
is.numeric(number) # ask whether "number" is numeric or not
```

    ## [1] TRUE

``` r
is.character(world) # ask whether "world" is character or not
```

    ## [1] TRUE

``` r
is.numeric(world) # ask whether "world" is numeric or not
```

    ## [1] FALSE

### 1.2.4. Special data type: NULL and NA

-   **Null** means an empty object: contain no information

-   **NA** means a non-available entry and representing a missing value
    in data analysis: contain information.

## 1.3. Vectors

A vector is an array of elements.We can create vectors in R with the
command **c()** and the elements inside separated by commas

**c()** is a generic function which can combines several arguments to
form a vector or list. There are no dimension in **c()**.

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
length(Example3)
```

    ## [1] 3

``` r
class(Example3)
```

    ## [1] "numeric"

### More information of numeric vectors

#### 1.3.1. Produce a consecutive numbers

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

We can use **seq()** to produce a continuous or regular sequence.

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

If we are going to repeat a sequence of number or a group of number,
**rep()** can generate a replicates value.

``` r
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
rep(c(3,2,1), time=c(2,1,3))
```

    ## [1] 3 3 2 1 1 1

``` r
rep(seq(0,1000, by=25), each=10)
```

    ##   [1]    0    0    0    0    0    0    0    0    0    0   25   25   25   25   25
    ##  [16]   25   25   25   25   25   50   50   50   50   50   50   50   50   50   50
    ##  [31]   75   75   75   75   75   75   75   75   75   75  100  100  100  100  100
    ##  [46]  100  100  100  100  100  125  125  125  125  125  125  125  125  125  125
    ##  [61]  150  150  150  150  150  150  150  150  150  150  175  175  175  175  175
    ##  [76]  175  175  175  175  175  200  200  200  200  200  200  200  200  200  200
    ##  [91]  225  225  225  225  225  225  225  225  225  225  250  250  250  250  250
    ## [106]  250  250  250  250  250  275  275  275  275  275  275  275  275  275  275
    ## [121]  300  300  300  300  300  300  300  300  300  300  325  325  325  325  325
    ## [136]  325  325  325  325  325  350  350  350  350  350  350  350  350  350  350
    ## [151]  375  375  375  375  375  375  375  375  375  375  400  400  400  400  400
    ## [166]  400  400  400  400  400  425  425  425  425  425  425  425  425  425  425
    ## [181]  450  450  450  450  450  450  450  450  450  450  475  475  475  475  475
    ## [196]  475  475  475  475  475  500  500  500  500  500  500  500  500  500  500
    ## [211]  525  525  525  525  525  525  525  525  525  525  550  550  550  550  550
    ## [226]  550  550  550  550  550  575  575  575  575  575  575  575  575  575  575
    ## [241]  600  600  600  600  600  600  600  600  600  600  625  625  625  625  625
    ## [256]  625  625  625  625  625  650  650  650  650  650  650  650  650  650  650
    ## [271]  675  675  675  675  675  675  675  675  675  675  700  700  700  700  700
    ## [286]  700  700  700  700  700  725  725  725  725  725  725  725  725  725  725
    ## [301]  750  750  750  750  750  750  750  750  750  750  775  775  775  775  775
    ## [316]  775  775  775  775  775  800  800  800  800  800  800  800  800  800  800
    ## [331]  825  825  825  825  825  825  825  825  825  825  850  850  850  850  850
    ## [346]  850  850  850  850  850  875  875  875  875  875  875  875  875  875  875
    ## [361]  900  900  900  900  900  900  900  900  900  900  925  925  925  925  925
    ## [376]  925  925  925  925  925  950  950  950  950  950  950  950  950  950  950
    ## [391]  975  975  975  975  975  975  975  975  975  975 1000 1000 1000 1000 1000
    ## [406] 1000 1000 1000 1000 1000

#### 1.3.2. Label the names to the numeric vector

**names()** is a function to check or get the name of each object

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

``` r
total.rains <- sum(rains)
```

If you are going to select the element in vector -\> use “brackets” **\[
\]** - Bracket are used for indexing into a vector, matrix, array, list
and data frame. - Also called *extraction operators*, extract specific
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

#### 1.3.3. Logical vector

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
# any(),  checking whether the condition is satisfied by, at least, one element of the vector.
any(temperature>=29)
```

    ## [1] TRUE

``` r
# all(), checking whether the conditions are statisfied by all elements of the vector.
all(temperature>=29)
```

    ## [1] FALSE

``` r
# to select day whether the temperature is larger than 29 degree in rain vector
rains[temperature>=29]
```

    ## Tuesday  Friday 
    ##       5       2

#### 1.3.4. Order and sort the vector

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

# 2. Excercise

-   Please build two separate vectors for temperature and precipitation,
    each labeled with the name of the day of the week (Sunday to
    Saturday, 9/10-9/16).

    -   *Ensure that the data is referenced from the Taichung weather
        station*
    -   *Please refer to the data last week*

    1.  What were the average, maximum, and minimum temperatures in
        Taichung last week?

    2.  What was the total precipitation in Taichung last week?

    3.  How many days did precipitation exceed 30 mm in a day?
