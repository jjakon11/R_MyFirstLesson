# **Class 5:Data Tidy, Filtering**

# 1. Input the Data

``` r
Taidt <- read.csv("E:/Drive/2_lab/Edu5_Course/R_MyFirstLesson/R/5_DataTidy_Filtering/Attachment/Taichung2013_2023.csv")

head(Taidt)
```

# 2. Basic tidy data function

## 2.1 select()

Use **select()** to select the column.

``` r
Taidt1 <- select(Taidt, station, Y, M, D, tavg, tmax,
    tmin, prec)
head(Taidt1)

Taidt1.1 <- select(Taidt, -X, -YMD, -AvgWS, -AvgWD)
```

## 2.2. filter()

Use **filter()** to filter the variable in the specific column.

``` r
Taidt2 <- filter(Taidt1, Y <= 2017)
```

## 2.3. mutate()

Use **mutate()** to add one column.

``` r
Taidt3 <- mutate(Taidt2, YMD = paste(Y, M, D, sep = "_"))
head(Taidt3)
str(Taidt3)

Taidt4 <- mutate(Taidt3, station = as.character(station))
str(Taidt4)
```

## 2.4. rename()

Use **rename()** to rename the column name.

``` r
Taidt5 <- rename(Taidt4, precipitation = "prec")
```

# Excercise

The following exercise is going to prepare for your next week data.
Please use pipe to connect all your data.

1.  Input the data of **Taichung2013_2023.csv**.

2.  Please select “station”, “Y”, “M”, “D”, “tavg”, “tmax”, “tmin”, and
    “prec” in Taichung 2013-2023 climate data.

3.  Please filter 2013-2017 data and **out put** to .csv file.

4.  Please filter 2017-2023 data and **out put** to .csv file.

Please email one rmd file to my email:
<a href="mailto:jjakon11@gmail.com"
class="email"><em>jjakon11@gmail.com</em></a>

Chen-Chia Ku
