Cleaning_data
========================================================
author:Alán Ponce
date: 2022-07-19 
autosize: true 


<div align="center">
<img src="imgs/ia_center.jpeg" width=700 height=600>
</div>




Agenda
========================================================
type: section

- Quick recap
  - Tidyyverse
  - Importing data
- Cleaning data
- Conclusions
- Q&A


Here’s what messy data look like
========================================================



```r
weather <- readRDS("data/weather.rds")

# View the first 6 rows of data
head(weather)
```

```
  X year month           measure X1 X2 X3 X4 X5 X6 X7 X8 X9 X10 X11 X12 X13 X14
1 1 2014    12  Max.TemperatureF 64 42 51 43 42 45 38 29 49  48  39  39  42  45
2 2 2014    12 Mean.TemperatureF 52 38 44 37 34 42 30 24 39  43  36  35  37  39
3 3 2014    12  Min.TemperatureF 39 33 37 30 26 38 21 18 29  38  32  31  32  33
4 4 2014    12    Max.Dew.PointF 46 40 49 24 37 45 36 28 49  45  37  28  28  29
5 5 2014    12    MeanDew.PointF 40 27 42 21 25 40 20 16 41  39  31  27  26  27
6 6 2014    12     Min.DewpointF 26 17 24 13 12 36 -3  3 28  37  27  25  24  25
  X15 X16 X17 X18 X19 X20 X21 X22 X23 X24 X25 X26 X27 X28 X29 X30 X31
1  42  44  49  44  37  36  36  44  47  46  59  50  52  52  41  30  30
2  37  40  45  40  33  32  33  39  45  44  52  44  45  46  36  26  25
3  32  35  41  36  29  27  30  33  42  41  44  37  38  40  30  22  20
4  33  42  46  34  25  30  30  39  45  46  58  31  34  42  26  10   8
5  29  36  41  30  22  24  27  34  42  44  43  29  31  35  20   4   5
6  27  30  32  26  20  20  25  25  37  41  29  28  29  27  10  -6   1
```

Here’s what messy data look like
========================================================



```r
bmi <- read.csv("data/bmi_clean.csv")

# Check the class of bmi
class(bmi)
```

```
[1] "data.frame"
```

```r
# Check the dimensions of bmi
dim(bmi)
```

```
[1] 199  30
```

```r
# View the column names of bmi
names(bmi)
```

```
 [1] "Country" "Y1980"   "Y1981"   "Y1982"   "Y1983"   "Y1984"   "Y1985"  
 [8] "Y1986"   "Y1987"   "Y1988"   "Y1989"   "Y1990"   "Y1991"   "Y1992"  
[15] "Y1993"   "Y1994"   "Y1995"   "Y1996"   "Y1997"   "Y1998"   "Y1999"  
[22] "Y2000"   "Y2001"   "Y2002"   "Y2003"   "Y2004"   "Y2005"   "Y2006"  
[29] "Y2007"   "Y2008"  
```


Here’s what messy data look like
========================================================



```r
# Check the structure of bmi
str(bmi)
```

```
'data.frame':	199 obs. of  30 variables:
 $ Country: chr  "Afghanistan" "Albania" "Algeria" "Andorra" ...
 $ Y1980  : num  21.5 25.2 22.3 25.7 20.9 ...
 $ Y1981  : num  21.5 25.2 22.3 25.7 20.9 ...
 $ Y1982  : num  21.5 25.3 22.4 25.7 20.9 ...
 $ Y1983  : num  21.4 25.3 22.5 25.8 20.9 ...
 $ Y1984  : num  21.4 25.3 22.6 25.8 20.9 ...
 $ Y1985  : num  21.4 25.3 22.7 25.9 20.9 ...
 $ Y1986  : num  21.4 25.3 22.8 25.9 21 ...
 $ Y1987  : num  21.4 25.3 22.8 25.9 21 ...
 $ Y1988  : num  21.3 25.3 22.9 26 21 ...
 $ Y1989  : num  21.3 25.3 23 26 21.1 ...
 $ Y1990  : num  21.2 25.3 23 26.1 21.1 ...
 $ Y1991  : num  21.2 25.3 23.1 26.2 21.1 ...
 $ Y1992  : num  21.1 25.2 23.2 26.2 21.1 ...
 $ Y1993  : num  21.1 25.2 23.3 26.3 21.1 ...
 $ Y1994  : num  21 25.2 23.3 26.4 21.1 ...
 $ Y1995  : num  20.9 25.3 23.4 26.4 21.2 ...
 $ Y1996  : num  20.9 25.3 23.5 26.5 21.2 ...
 $ Y1997  : num  20.8 25.3 23.5 26.6 21.2 ...
 $ Y1998  : num  20.8 25.4 23.6 26.7 21.3 ...
 $ Y1999  : num  20.8 25.5 23.7 26.8 21.3 ...
 $ Y2000  : num  20.7 25.6 23.8 26.8 21.4 ...
 $ Y2001  : num  20.6 25.7 23.9 26.9 21.4 ...
 $ Y2002  : num  20.6 25.8 24 27 21.5 ...
 $ Y2003  : num  20.6 25.9 24.1 27.1 21.6 ...
 $ Y2004  : num  20.6 26 24.2 27.2 21.7 ...
 $ Y2005  : num  20.6 26.1 24.3 27.3 21.8 ...
 $ Y2006  : num  20.6 26.2 24.4 27.4 21.9 ...
 $ Y2007  : num  20.6 26.3 24.5 27.5 22.1 ...
 $ Y2008  : num  20.6 26.4 24.6 27.6 22.3 ...
```

Here’s what messy data look like
========================================================



```r
# Check the structure of bmi, the dplyr way
glimpse(bmi)
```

```
Rows: 199
Columns: 30
$ Country <chr> "Afghanistan", "Albania", "Algeria", "Andorra", "Angola", "Ant…
$ Y1980   <dbl> 21.48678, 25.22533, 22.25703, 25.66652, 20.94876, 23.31424, 25…
$ Y1981   <dbl> 21.46552, 25.23981, 22.34745, 25.70868, 20.94371, 23.39054, 25…
$ Y1982   <dbl> 21.45145, 25.25636, 22.43647, 25.74681, 20.93754, 23.45883, 25…
$ Y1983   <dbl> 21.43822, 25.27176, 22.52105, 25.78250, 20.93187, 23.53735, 25…
$ Y1984   <dbl> 21.42734, 25.27901, 22.60633, 25.81874, 20.93569, 23.63584, 25…
$ Y1985   <dbl> 21.41222, 25.28669, 22.69501, 25.85236, 20.94857, 23.73109, 25…
$ Y1986   <dbl> 21.40132, 25.29451, 22.76979, 25.89089, 20.96030, 23.83449, 25…
$ Y1987   <dbl> 21.37679, 25.30217, 22.84096, 25.93414, 20.98025, 23.93649, 25…
$ Y1988   <dbl> 21.34018, 25.30450, 22.90644, 25.98477, 21.01375, 24.05364, 25…
$ Y1989   <dbl> 21.29845, 25.31944, 22.97931, 26.04450, 21.05269, 24.16347, 25…
$ Y1990   <dbl> 21.24818, 25.32357, 23.04600, 26.10936, 21.09007, 24.26782, 25…
$ Y1991   <dbl> 21.20269, 25.28452, 23.11333, 26.17912, 21.12136, 24.36568, 25…
$ Y1992   <dbl> 21.14238, 25.23077, 23.18776, 26.24017, 21.14987, 24.45644, 26…
$ Y1993   <dbl> 21.06376, 25.21192, 23.25764, 26.30356, 21.13938, 24.54096, 26…
$ Y1994   <dbl> 20.97987, 25.22115, 23.32273, 26.36793, 21.14186, 24.60945, 26…
$ Y1995   <dbl> 20.91132, 25.25874, 23.39526, 26.43569, 21.16022, 24.66461, 26…
$ Y1996   <dbl> 20.85155, 25.31097, 23.46811, 26.50769, 21.19076, 24.72544, 26…
$ Y1997   <dbl> 20.81307, 25.33988, 23.54160, 26.58255, 21.22621, 24.78714, 26…
$ Y1998   <dbl> 20.78591, 25.39116, 23.61592, 26.66337, 21.27082, 24.84936, 26…
$ Y1999   <dbl> 20.75469, 25.46555, 23.69486, 26.75078, 21.31954, 24.91721, 26…
$ Y2000   <dbl> 20.69521, 25.55835, 23.77659, 26.83179, 21.37480, 24.99158, 26…
$ Y2001   <dbl> 20.62643, 25.66701, 23.86256, 26.92373, 21.43664, 25.05857, 26…
$ Y2002   <dbl> 20.59848, 25.77167, 23.95294, 27.02525, 21.51765, 25.13039, 26…
$ Y2003   <dbl> 20.58706, 25.87274, 24.05243, 27.12481, 21.59924, 25.20713, 27…
$ Y2004   <dbl> 20.57759, 25.98136, 24.15957, 27.23107, 21.69218, 25.29898, 27…
$ Y2005   <dbl> 20.58084, 26.08939, 24.27001, 27.32827, 21.80564, 25.39965, 27…
$ Y2006   <dbl> 20.58749, 26.20867, 24.38270, 27.43588, 21.93881, 25.51382, 27…
$ Y2007   <dbl> 20.60246, 26.32753, 24.48846, 27.53363, 22.08962, 25.64247, 27…
$ Y2008   <dbl> 20.62058, 26.44657, 24.59620, 27.63048, 22.25083, 25.76602, 27…
```

Here’s what messy data look like
========================================================



```r
# View a summary of bmi
summary(bmi)
```

```
   Country              Y1980           Y1981           Y1982      
 Length:199         Min.   :19.01   Min.   :19.04   Min.   :19.07  
 Class :character   1st Qu.:21.27   1st Qu.:21.31   1st Qu.:21.36  
 Mode  :character   Median :23.31   Median :23.39   Median :23.46  
                    Mean   :23.15   Mean   :23.21   Mean   :23.26  
                    3rd Qu.:24.82   3rd Qu.:24.89   3rd Qu.:24.94  
                    Max.   :28.12   Max.   :28.36   Max.   :28.58  
     Y1983           Y1984           Y1985           Y1986      
 Min.   :19.10   Min.   :19.13   Min.   :19.16   Min.   :19.20  
 1st Qu.:21.42   1st Qu.:21.45   1st Qu.:21.47   1st Qu.:21.49  
 Median :23.57   Median :23.64   Median :23.73   Median :23.82  
 Mean   :23.32   Mean   :23.37   Mean   :23.42   Mean   :23.48  
 3rd Qu.:25.02   3rd Qu.:25.06   3rd Qu.:25.11   3rd Qu.:25.20  
 Max.   :28.82   Max.   :29.05   Max.   :29.28   Max.   :29.52  
     Y1987           Y1988           Y1989           Y1990      
 Min.   :19.23   Min.   :19.27   Min.   :19.31   Min.   :19.35  
 1st Qu.:21.50   1st Qu.:21.52   1st Qu.:21.55   1st Qu.:21.57  
 Median :23.87   Median :23.93   Median :24.03   Median :24.14  
 Mean   :23.53   Mean   :23.59   Mean   :23.65   Mean   :23.71  
 3rd Qu.:25.27   3rd Qu.:25.34   3rd Qu.:25.37   3rd Qu.:25.39  
 Max.   :29.75   Max.   :29.98   Max.   :30.20   Max.   :30.42  
     Y1991           Y1992           Y1993           Y1994      
 Min.   :19.40   Min.   :19.45   Min.   :19.51   Min.   :19.59  
 1st Qu.:21.60   1st Qu.:21.65   1st Qu.:21.74   1st Qu.:21.76  
 Median :24.20   Median :24.19   Median :24.27   Median :24.36  
 Mean   :23.76   Mean   :23.82   Mean   :23.88   Mean   :23.94  
 3rd Qu.:25.42   3rd Qu.:25.48   3rd Qu.:25.54   3rd Qu.:25.62  
 Max.   :30.64   Max.   :30.85   Max.   :31.04   Max.   :31.23  
     Y1995           Y1996           Y1997           Y1998      
 Min.   :19.67   Min.   :19.71   Min.   :19.74   Min.   :19.77  
 1st Qu.:21.83   1st Qu.:21.89   1st Qu.:21.94   1st Qu.:22.00  
 Median :24.41   Median :24.42   Median :24.50   Median :24.49  
 Mean   :24.00   Mean   :24.07   Mean   :24.14   Mean   :24.21  
 3rd Qu.:25.70   3rd Qu.:25.78   3rd Qu.:25.85   3rd Qu.:25.94  
 Max.   :31.41   Max.   :31.59   Max.   :31.77   Max.   :31.95  
     Y1999           Y2000           Y2001           Y2002      
 Min.   :19.80   Min.   :19.83   Min.   :19.86   Min.   :19.84  
 1st Qu.:22.04   1st Qu.:22.12   1st Qu.:22.22   1st Qu.:22.29  
 Median :24.61   Median :24.66   Median :24.73   Median :24.81  
 Mean   :24.29   Mean   :24.36   Mean   :24.44   Mean   :24.52  
 3rd Qu.:26.01   3rd Qu.:26.09   3rd Qu.:26.19   3rd Qu.:26.30  
 Max.   :32.13   Max.   :32.32   Max.   :32.51   Max.   :32.70  
     Y2003           Y2004           Y2005           Y2006      
 Min.   :19.81   Min.   :19.79   Min.   :19.79   Min.   :19.80  
 1st Qu.:22.37   1st Qu.:22.45   1st Qu.:22.54   1st Qu.:22.63  
 Median :24.89   Median :25.00   Median :25.11   Median :25.24  
 Mean   :24.61   Mean   :24.70   Mean   :24.79   Mean   :24.89  
 3rd Qu.:26.38   3rd Qu.:26.47   3rd Qu.:26.53   3rd Qu.:26.59  
 Max.   :32.90   Max.   :33.10   Max.   :33.30   Max.   :33.49  
     Y2007           Y2008      
 Min.   :19.83   Min.   :19.87  
 1st Qu.:22.73   1st Qu.:22.83  
 Median :25.36   Median :25.50  
 Mean   :24.99   Mean   :25.10  
 3rd Qu.:26.66   3rd Qu.:26.82  
 Max.   :33.69   Max.   :33.90  
```

Visualizing your data
========================================================



```r
# Histogram of BMIs from 2008
hist(bmi$Y2008)
```

![plot of chunk unnamed-chunk-7](Cleaning_data-figure/unnamed-chunk-7-1.png)

Visualizing your data
========================================================


```r
# Scatter plot comparing BMIs from 1980 to those from 2008
plot(bmi$Y1980, bmi$Y2008)
```

![plot of chunk unnamed-chunk-8](Cleaning_data-figure/unnamed-chunk-8-1.png)


Gathering columns into key-value pairs
========================================================


```r
head(bmi)
```

```
              Country    Y1980    Y1981    Y1982    Y1983    Y1984    Y1985
1         Afghanistan 21.48678 21.46552 21.45145 21.43822 21.42734 21.41222
2             Albania 25.22533 25.23981 25.25636 25.27176 25.27901 25.28669
3             Algeria 22.25703 22.34745 22.43647 22.52105 22.60633 22.69501
4             Andorra 25.66652 25.70868 25.74681 25.78250 25.81874 25.85236
5              Angola 20.94876 20.94371 20.93754 20.93187 20.93569 20.94857
6 Antigua and Barbuda 23.31424 23.39054 23.45883 23.53735 23.63584 23.73109
     Y1986    Y1987    Y1988    Y1989    Y1990    Y1991    Y1992    Y1993
1 21.40132 21.37679 21.34018 21.29845 21.24818 21.20269 21.14238 21.06376
2 25.29451 25.30217 25.30450 25.31944 25.32357 25.28452 25.23077 25.21192
3 22.76979 22.84096 22.90644 22.97931 23.04600 23.11333 23.18776 23.25764
4 25.89089 25.93414 25.98477 26.04450 26.10936 26.17912 26.24017 26.30356
5 20.96030 20.98025 21.01375 21.05269 21.09007 21.12136 21.14987 21.13938
6 23.83449 23.93649 24.05364 24.16347 24.26782 24.36568 24.45644 24.54096
     Y1994    Y1995    Y1996    Y1997    Y1998    Y1999    Y2000    Y2001
1 20.97987 20.91132 20.85155 20.81307 20.78591 20.75469 20.69521 20.62643
2 25.22115 25.25874 25.31097 25.33988 25.39116 25.46555 25.55835 25.66701
3 23.32273 23.39526 23.46811 23.54160 23.61592 23.69486 23.77659 23.86256
4 26.36793 26.43569 26.50769 26.58255 26.66337 26.75078 26.83179 26.92373
5 21.14186 21.16022 21.19076 21.22621 21.27082 21.31954 21.37480 21.43664
6 24.60945 24.66461 24.72544 24.78714 24.84936 24.91721 24.99158 25.05857
     Y2002    Y2003    Y2004    Y2005    Y2006    Y2007    Y2008
1 20.59848 20.58706 20.57759 20.58084 20.58749 20.60246 20.62058
2 25.77167 25.87274 25.98136 26.08939 26.20867 26.32753 26.44657
3 23.95294 24.05243 24.15957 24.27001 24.38270 24.48846 24.59620
4 27.02525 27.12481 27.23107 27.32827 27.43588 27.53363 27.63048
5 21.51765 21.59924 21.69218 21.80564 21.93881 22.08962 22.25083
6 25.13039 25.20713 25.29898 25.39965 25.51382 25.64247 25.76602
```

Gathering columns into key-value pairs
========================================================


```r
# Apply gather() to bmi and save the result as bmi_long
bmi_long <- gather(bmi, 
                   year, bmi_val, 
                   -Country)

# View the first 20 rows of the result
head(bmi_long, 10)
```

```
               Country  year  bmi_val
1          Afghanistan Y1980 21.48678
2              Albania Y1980 25.22533
3              Algeria Y1980 22.25703
4              Andorra Y1980 25.66652
5               Angola Y1980 20.94876
6  Antigua and Barbuda Y1980 23.31424
7            Argentina Y1980 25.37913
8              Armenia Y1980 23.82469
9            Australia Y1980 24.92729
10             Austria Y1980 24.84097
```


Spreading key-value pairs into columns
========================================================


```r
# Apply spread() to bmi_long
bmi_wide <- spread(bmi_long, year, bmi_val)

# View the head of bmi_wide
head(bmi_wide)
```

```
              Country    Y1980    Y1981    Y1982    Y1983    Y1984    Y1985
1         Afghanistan 21.48678 21.46552 21.45145 21.43822 21.42734 21.41222
2             Albania 25.22533 25.23981 25.25636 25.27176 25.27901 25.28669
3             Algeria 22.25703 22.34745 22.43647 22.52105 22.60633 22.69501
4             Andorra 25.66652 25.70868 25.74681 25.78250 25.81874 25.85236
5              Angola 20.94876 20.94371 20.93754 20.93187 20.93569 20.94857
6 Antigua and Barbuda 23.31424 23.39054 23.45883 23.53735 23.63584 23.73109
     Y1986    Y1987    Y1988    Y1989    Y1990    Y1991    Y1992    Y1993
1 21.40132 21.37679 21.34018 21.29845 21.24818 21.20269 21.14238 21.06376
2 25.29451 25.30217 25.30450 25.31944 25.32357 25.28452 25.23077 25.21192
3 22.76979 22.84096 22.90644 22.97931 23.04600 23.11333 23.18776 23.25764
4 25.89089 25.93414 25.98477 26.04450 26.10936 26.17912 26.24017 26.30356
5 20.96030 20.98025 21.01375 21.05269 21.09007 21.12136 21.14987 21.13938
6 23.83449 23.93649 24.05364 24.16347 24.26782 24.36568 24.45644 24.54096
     Y1994    Y1995    Y1996    Y1997    Y1998    Y1999    Y2000    Y2001
1 20.97987 20.91132 20.85155 20.81307 20.78591 20.75469 20.69521 20.62643
2 25.22115 25.25874 25.31097 25.33988 25.39116 25.46555 25.55835 25.66701
3 23.32273 23.39526 23.46811 23.54160 23.61592 23.69486 23.77659 23.86256
4 26.36793 26.43569 26.50769 26.58255 26.66337 26.75078 26.83179 26.92373
5 21.14186 21.16022 21.19076 21.22621 21.27082 21.31954 21.37480 21.43664
6 24.60945 24.66461 24.72544 24.78714 24.84936 24.91721 24.99158 25.05857
     Y2002    Y2003    Y2004    Y2005    Y2006    Y2007    Y2008
1 20.59848 20.58706 20.57759 20.58084 20.58749 20.60246 20.62058
2 25.77167 25.87274 25.98136 26.08939 26.20867 26.32753 26.44657
3 23.95294 24.05243 24.15957 24.27001 24.38270 24.48846 24.59620
4 27.02525 27.12481 27.23107 27.32827 27.43588 27.53363 27.63048
5 21.51765 21.59924 21.69218 21.80564 21.93881 22.08962 22.25083
6 25.13039 25.20713 25.29898 25.39965 25.51382 25.64247 25.76602
```



Separating columns
========================================================


```r
patient <- rep(c('X','Y'),3)

treatment <- rep(c('A','B'),3)

year_mo <- c(rep(c('2010-10'),2),
             rep(c('2012-08'),2),
             rep(c('2014-12'),2)
             )

response <- c(1,4,2,5,3,6)

treatments <- data.frame(patient, treatment, year_mo, response)

treatments
```

```
  patient treatment year_mo response
1       X         A 2010-10        1
2       Y         B 2010-10        4
3       X         A 2012-08        2
4       Y         B 2012-08        5
5       X         A 2014-12        3
6       Y         B 2014-12        6
```



Separating columns
========================================================


```r
# separate one column into multiple columns
# the sep argument
#   any character <> letter or number
#   or specify a specific separator
treatments_sep <- separate(treatments, 
                           col = year_mo, 
                           into = c("year", "month"))
                           # sep = "/"
treatments_sep
```

```
  patient treatment year month response
1       X         A 2010    10        1
2       Y         B 2010    10        4
3       X         A 2012    08        2
4       Y         B 2012    08        5
5       X         A 2014    12        3
6       Y         B 2014    12        6
```

Uniting columns
========================================================


```r
treatments_uni <- unite(treatments_sep, 
                                      year_mo, 
                                      year, month)

treatments_uni
```

```
  patient treatment year_mo response
1       X         A 2010_10        1
2       Y         B 2010_10        4
3       X         A 2012_08        2
4       Y         B 2012_08        5
5       X         A 2014_12        3
6       Y         B 2014_12        6
```


Uniting columns
========================================================


```r
bmi_cc_clean <- read.csv("data/bmi_cc_clean.csv")

head(bmi_cc_clean)
```

```
              Country ISO    Y1980    Y1981    Y1982    Y1983    Y1984    Y1985
1         Afghanistan  AF 21.48678 21.46552 21.45145 21.43822 21.42734 21.41222
2             Albania  AL 25.22533 25.23981 25.25636 25.27176 25.27901 25.28669
3             Algeria  DZ 22.25703 22.34745 22.43647 22.52105 22.60633 22.69501
4             Andorra  AD 25.66652 25.70868 25.74681 25.78250 25.81874 25.85236
5              Angola  AO 20.94876 20.94371 20.93754 20.93187 20.93569 20.94857
6 Antigua and Barbuda  AG 23.31424 23.39054 23.45883 23.53735 23.63584 23.73109
     Y1986    Y1987    Y1988    Y1989    Y1990    Y1991    Y1992    Y1993
1 21.40132 21.37679 21.34018 21.29845 21.24818 21.20269 21.14238 21.06376
2 25.29451 25.30217 25.30450 25.31944 25.32357 25.28452 25.23077 25.21192
3 22.76979 22.84096 22.90644 22.97931 23.04600 23.11333 23.18776 23.25764
4 25.89089 25.93414 25.98477 26.04450 26.10936 26.17912 26.24017 26.30356
5 20.96030 20.98025 21.01375 21.05269 21.09007 21.12136 21.14987 21.13938
6 23.83449 23.93649 24.05364 24.16347 24.26782 24.36568 24.45644 24.54096
     Y1994    Y1995    Y1996    Y1997    Y1998    Y1999    Y2000    Y2001
1 20.97987 20.91132 20.85155 20.81307 20.78591 20.75469 20.69521 20.62643
2 25.22115 25.25874 25.31097 25.33988 25.39116 25.46555 25.55835 25.66701
3 23.32273 23.39526 23.46811 23.54160 23.61592 23.69486 23.77659 23.86256
4 26.36793 26.43569 26.50769 26.58255 26.66337 26.75078 26.83179 26.92373
5 21.14186 21.16022 21.19076 21.22621 21.27082 21.31954 21.37480 21.43664
6 24.60945 24.66461 24.72544 24.78714 24.84936 24.91721 24.99158 25.05857
     Y2002    Y2003    Y2004    Y2005    Y2006    Y2007    Y2008
1 20.59848 20.58706 20.57759 20.58084 20.58749 20.60246 20.62058
2 25.77167 25.87274 25.98136 26.08939 26.20867 26.32753 26.44657
3 23.95294 24.05243 24.15957 24.27001 24.38270 24.48846 24.59620
4 27.02525 27.12481 27.23107 27.32827 27.43588 27.53363 27.63048
5 21.51765 21.59924 21.69218 21.80564 21.93881 22.08962 22.25083
6 25.13039 25.20713 25.29898 25.39965 25.51382 25.64247 25.76602
```


Uniting columns
========================================================


```r
# Apply unite() to bmi_cc_clean
bmi_cc <- unite(bmi_cc_clean, 
                            Country_ISO, 
                            Country, ISO, sep = "-")

# View the head of the result
head(bmi_cc)
```

```
             Country_ISO    Y1980    Y1981    Y1982    Y1983    Y1984    Y1985
1         Afghanistan-AF 21.48678 21.46552 21.45145 21.43822 21.42734 21.41222
2             Albania-AL 25.22533 25.23981 25.25636 25.27176 25.27901 25.28669
3             Algeria-DZ 22.25703 22.34745 22.43647 22.52105 22.60633 22.69501
4             Andorra-AD 25.66652 25.70868 25.74681 25.78250 25.81874 25.85236
5              Angola-AO 20.94876 20.94371 20.93754 20.93187 20.93569 20.94857
6 Antigua and Barbuda-AG 23.31424 23.39054 23.45883 23.53735 23.63584 23.73109
     Y1986    Y1987    Y1988    Y1989    Y1990    Y1991    Y1992    Y1993
1 21.40132 21.37679 21.34018 21.29845 21.24818 21.20269 21.14238 21.06376
2 25.29451 25.30217 25.30450 25.31944 25.32357 25.28452 25.23077 25.21192
3 22.76979 22.84096 22.90644 22.97931 23.04600 23.11333 23.18776 23.25764
4 25.89089 25.93414 25.98477 26.04450 26.10936 26.17912 26.24017 26.30356
5 20.96030 20.98025 21.01375 21.05269 21.09007 21.12136 21.14987 21.13938
6 23.83449 23.93649 24.05364 24.16347 24.26782 24.36568 24.45644 24.54096
     Y1994    Y1995    Y1996    Y1997    Y1998    Y1999    Y2000    Y2001
1 20.97987 20.91132 20.85155 20.81307 20.78591 20.75469 20.69521 20.62643
2 25.22115 25.25874 25.31097 25.33988 25.39116 25.46555 25.55835 25.66701
3 23.32273 23.39526 23.46811 23.54160 23.61592 23.69486 23.77659 23.86256
4 26.36793 26.43569 26.50769 26.58255 26.66337 26.75078 26.83179 26.92373
5 21.14186 21.16022 21.19076 21.22621 21.27082 21.31954 21.37480 21.43664
6 24.60945 24.66461 24.72544 24.78714 24.84936 24.91721 24.99158 25.05857
     Y2002    Y2003    Y2004    Y2005    Y2006    Y2007    Y2008
1 20.59848 20.58706 20.57759 20.58084 20.58749 20.60246 20.62058
2 25.77167 25.87274 25.98136 26.08939 26.20867 26.32753 26.44657
3 23.95294 24.05243 24.15957 24.27001 24.38270 24.48846 24.59620
4 27.02525 27.12481 27.23107 27.32827 27.43588 27.53363 27.63048
5 21.51765 21.59924 21.69218 21.80564 21.93881 22.08962 22.25083
6 25.13039 25.20713 25.29898 25.39965 25.51382 25.64247 25.76602
```


Separating columns
========================================================


```r
# Apply separate() to bmi_cc
bmi_cc_clean2 <- separate(bmi_cc, col = Country_ISO, into = c("Country", "ISO"), sep = "-")

# View the head of the result
head(bmi_cc_clean2)
```

```
              Country ISO    Y1980    Y1981    Y1982    Y1983    Y1984    Y1985
1         Afghanistan  AF 21.48678 21.46552 21.45145 21.43822 21.42734 21.41222
2             Albania  AL 25.22533 25.23981 25.25636 25.27176 25.27901 25.28669
3             Algeria  DZ 22.25703 22.34745 22.43647 22.52105 22.60633 22.69501
4             Andorra  AD 25.66652 25.70868 25.74681 25.78250 25.81874 25.85236
5              Angola  AO 20.94876 20.94371 20.93754 20.93187 20.93569 20.94857
6 Antigua and Barbuda  AG 23.31424 23.39054 23.45883 23.53735 23.63584 23.73109
     Y1986    Y1987    Y1988    Y1989    Y1990    Y1991    Y1992    Y1993
1 21.40132 21.37679 21.34018 21.29845 21.24818 21.20269 21.14238 21.06376
2 25.29451 25.30217 25.30450 25.31944 25.32357 25.28452 25.23077 25.21192
3 22.76979 22.84096 22.90644 22.97931 23.04600 23.11333 23.18776 23.25764
4 25.89089 25.93414 25.98477 26.04450 26.10936 26.17912 26.24017 26.30356
5 20.96030 20.98025 21.01375 21.05269 21.09007 21.12136 21.14987 21.13938
6 23.83449 23.93649 24.05364 24.16347 24.26782 24.36568 24.45644 24.54096
     Y1994    Y1995    Y1996    Y1997    Y1998    Y1999    Y2000    Y2001
1 20.97987 20.91132 20.85155 20.81307 20.78591 20.75469 20.69521 20.62643
2 25.22115 25.25874 25.31097 25.33988 25.39116 25.46555 25.55835 25.66701
3 23.32273 23.39526 23.46811 23.54160 23.61592 23.69486 23.77659 23.86256
4 26.36793 26.43569 26.50769 26.58255 26.66337 26.75078 26.83179 26.92373
5 21.14186 21.16022 21.19076 21.22621 21.27082 21.31954 21.37480 21.43664
6 24.60945 24.66461 24.72544 24.78714 24.84936 24.91721 24.99158 25.05857
     Y2002    Y2003    Y2004    Y2005    Y2006    Y2007    Y2008
1 20.59848 20.58706 20.57759 20.58084 20.58749 20.60246 20.62058
2 25.77167 25.87274 25.98136 26.08939 26.20867 26.32753 26.44657
3 23.95294 24.05243 24.15957 24.27001 24.38270 24.48846 24.59620
4 27.02525 27.12481 27.23107 27.32827 27.43588 27.53363 27.63048
5 21.51765 21.59924 21.69218 21.80564 21.93881 22.08962 22.25083
6 25.13039 25.20713 25.29898 25.39965 25.51382 25.64247 25.76602
```



Column headers are values, not variable names
========================================================


```r
census <- read.csv("data/census-retail.csv")

# View the head of census
head(census)
```

```
  YEAR    JAN    FEB    MAR    APR    MAY    JUN    JUL    AUG    SEP    OCT
1 1992 146913 147270 146831 148082 149015 149821 150809 151064 152595 153577
2 1993 157525 156292 154774 158996 160624 160171 162832 162491 163285 164711
3 1994 167504 169652 172775 173099 172340 174307 174801 177289 178776 180569
4 1995 182423 179472 180996 181702 183543 186088 185470 186814 187338 186546
5 1996 189167 192269 193993 194712 196210 196127 196229 196215 198843 200488
6 1997 202414 204273 204965 203372 201676 204666 207049 207643 208298 208064
     NOV    DEC
1 153605 155504
2 166593 168101
3 180695 181492
4 189052 190809
5 200200 201191
6 208982 209379
```


Column headers are values, not variable names
========================================================


```r
# Gather the month columns
census2 <- gather(census, month, amount, -YEAR)

# Arrange rows by YEAR using dplyr's arrange
census2 <- arrange(census2, YEAR)

# View first 20 rows of census2
head(census2, 20)
```

```
   YEAR month amount
1  1992   JAN 146913
2  1992   FEB 147270
3  1992   MAR 146831
4  1992   APR 148082
5  1992   MAY 149015
6  1992   JUN 149821
7  1992   JUL 150809
8  1992   AUG 151064
9  1992   SEP 152595
10 1992   OCT 153577
11 1992   NOV 153605
12 1992   DEC 155504
13 1993   JAN 157525
14 1993   FEB 156292
15 1993   MAR 154774
16 1993   APR 158996
17 1993   MAY 160624
18 1993   JUN 160171
19 1993   JUL 162832
20 1993   AUG 162491
```


Common type conversions
========================================================

- source <http://archive.ics.uci.edu/ml/datasets/Student+Performance>


```r
students <- read.csv("data/students.csv")

#head(students)

# Preview students with str()
str(students)
```

```
'data.frame':	395 obs. of  31 variables:
 $ school    : chr  "GP" "GP" "GP" "GP" ...
 $ sex       : chr  "F" "F" "F" "F" ...
 $ age       : int  18 17 15 15 16 16 16 17 15 15 ...
 $ address   : chr  "U" "U" "U" "U" ...
 $ famsize   : chr  "GT3" "GT3" "LE3" "GT3" ...
 $ Pstatus   : chr  "A" "T" "T" "T" ...
 $ Medu      : int  4 1 1 4 3 4 2 4 3 3 ...
 $ Fedu      : int  4 1 1 2 3 3 2 4 2 4 ...
 $ Mjob      : chr  "at_home" "at_home" "at_home" "health" ...
 $ Fjob      : chr  "teacher" "other" "other" "services" ...
 $ reason    : chr  "course" "course" "other" "home" ...
 $ guardian  : chr  "mother" "father" "mother" "mother" ...
 $ traveltime: int  2 1 1 1 1 1 1 2 1 1 ...
 $ studytime : int  2 2 2 3 2 2 2 2 2 2 ...
 $ failures  : int  0 0 3 0 0 0 0 0 0 0 ...
 $ schoolsup : chr  "yes" "no" "yes" "no" ...
 $ famsup    : chr  "no" "yes" "no" "yes" ...
 $ paid      : chr  "no" "no" "yes" "yes" ...
 $ activities: chr  "no" "no" "no" "yes" ...
 $ nursery   : chr  "yes" "no" "yes" "yes" ...
 $ higher    : chr  "yes" "yes" "yes" "yes" ...
 $ internet  : chr  "no" "yes" "yes" "yes" ...
 $ romantic  : chr  "no" "no" "no" "yes" ...
 $ famrel    : int  4 5 4 3 4 5 4 4 4 5 ...
 $ freetime  : int  3 3 3 2 3 4 4 1 2 5 ...
 $ goout     : int  4 3 2 2 2 2 4 4 2 1 ...
 $ Dalc      : int  1 1 2 1 1 1 1 1 1 1 ...
 $ Walc      : int  1 1 3 1 2 2 1 1 1 1 ...
 $ health    : int  3 3 3 5 5 5 3 1 1 5 ...
 $ absences  : int  6 4 10 2 4 10 0 6 0 0 ...
 $ Grades    : chr  "5/6/6" "5/5/6" "7/8/10" "15/14/15" ...
```


Common type conversions
========================================================


```r
#7 Medu - mother's education (numeric: 0 - none, 1 - primary education (4th grade), 2 â€“ 5th to 9th grade, 3 â€“ secondary education or 4 â€“ higher education)


# Coerce Medu to factor
students$Medu <- as.factor(students$Medu)

# Preview students with str()
str(students)
```

```
'data.frame':	395 obs. of  31 variables:
 $ school    : chr  "GP" "GP" "GP" "GP" ...
 $ sex       : chr  "F" "F" "F" "F" ...
 $ age       : int  18 17 15 15 16 16 16 17 15 15 ...
 $ address   : chr  "U" "U" "U" "U" ...
 $ famsize   : chr  "GT3" "GT3" "LE3" "GT3" ...
 $ Pstatus   : chr  "A" "T" "T" "T" ...
 $ Medu      : Factor w/ 5 levels "0","1","2","3",..: 5 2 2 5 4 5 3 5 4 4 ...
 $ Fedu      : int  4 1 1 2 3 3 2 4 2 4 ...
 $ Mjob      : chr  "at_home" "at_home" "at_home" "health" ...
 $ Fjob      : chr  "teacher" "other" "other" "services" ...
 $ reason    : chr  "course" "course" "other" "home" ...
 $ guardian  : chr  "mother" "father" "mother" "mother" ...
 $ traveltime: int  2 1 1 1 1 1 1 2 1 1 ...
 $ studytime : int  2 2 2 3 2 2 2 2 2 2 ...
 $ failures  : int  0 0 3 0 0 0 0 0 0 0 ...
 $ schoolsup : chr  "yes" "no" "yes" "no" ...
 $ famsup    : chr  "no" "yes" "no" "yes" ...
 $ paid      : chr  "no" "no" "yes" "yes" ...
 $ activities: chr  "no" "no" "no" "yes" ...
 $ nursery   : chr  "yes" "no" "yes" "yes" ...
 $ higher    : chr  "yes" "yes" "yes" "yes" ...
 $ internet  : chr  "no" "yes" "yes" "yes" ...
 $ romantic  : chr  "no" "no" "no" "yes" ...
 $ famrel    : int  4 5 4 3 4 5 4 4 4 5 ...
 $ freetime  : int  3 3 3 2 3 4 4 1 2 5 ...
 $ goout     : int  4 3 2 2 2 2 4 4 2 1 ...
 $ Dalc      : int  1 1 2 1 1 1 1 1 1 1 ...
 $ Walc      : int  1 1 3 1 2 2 1 1 1 1 ...
 $ health    : int  3 3 3 5 5 5 3 1 1 5 ...
 $ absences  : int  6 4 10 2 4 10 0 6 0 0 ...
 $ Grades    : chr  "5/6/6" "5/5/6" "7/8/10" "15/14/15" ...
```

Common type conversions
========================================================


```r
#8 Fedu - father's education (numeric: 0 - none, 1 - primary education (4th grade), 2 â€“ 5th to 9th grade, 3 â€“ secondary education or 4 â€“ higher education)

# Coerce Fedu to factor
students$Fedu <- as.factor(students$Fedu)

# Preview students with str()
str(students)
```

```
'data.frame':	395 obs. of  31 variables:
 $ school    : chr  "GP" "GP" "GP" "GP" ...
 $ sex       : chr  "F" "F" "F" "F" ...
 $ age       : int  18 17 15 15 16 16 16 17 15 15 ...
 $ address   : chr  "U" "U" "U" "U" ...
 $ famsize   : chr  "GT3" "GT3" "LE3" "GT3" ...
 $ Pstatus   : chr  "A" "T" "T" "T" ...
 $ Medu      : Factor w/ 5 levels "0","1","2","3",..: 5 2 2 5 4 5 3 5 4 4 ...
 $ Fedu      : Factor w/ 5 levels "0","1","2","3",..: 5 2 2 3 4 4 3 5 3 5 ...
 $ Mjob      : chr  "at_home" "at_home" "at_home" "health" ...
 $ Fjob      : chr  "teacher" "other" "other" "services" ...
 $ reason    : chr  "course" "course" "other" "home" ...
 $ guardian  : chr  "mother" "father" "mother" "mother" ...
 $ traveltime: int  2 1 1 1 1 1 1 2 1 1 ...
 $ studytime : int  2 2 2 3 2 2 2 2 2 2 ...
 $ failures  : int  0 0 3 0 0 0 0 0 0 0 ...
 $ schoolsup : chr  "yes" "no" "yes" "no" ...
 $ famsup    : chr  "no" "yes" "no" "yes" ...
 $ paid      : chr  "no" "no" "yes" "yes" ...
 $ activities: chr  "no" "no" "no" "yes" ...
 $ nursery   : chr  "yes" "no" "yes" "yes" ...
 $ higher    : chr  "yes" "yes" "yes" "yes" ...
 $ internet  : chr  "no" "yes" "yes" "yes" ...
 $ romantic  : chr  "no" "no" "no" "yes" ...
 $ famrel    : int  4 5 4 3 4 5 4 4 4 5 ...
 $ freetime  : int  3 3 3 2 3 4 4 1 2 5 ...
 $ goout     : int  4 3 2 2 2 2 4 4 2 1 ...
 $ Dalc      : int  1 1 2 1 1 1 1 1 1 1 ...
 $ Walc      : int  1 1 3 1 2 2 1 1 1 1 ...
 $ health    : int  3 3 3 5 5 5 3 1 1 5 ...
 $ absences  : int  6 4 10 2 4 10 0 6 0 0 ...
 $ Grades    : chr  "5/6/6" "5/5/6" "7/8/10" "15/14/15" ...
```

```r
# https://www.r-bloggers.com/2020/02/a-guide-to-encoding-categorical-features-using-r/
```

Working with dates
========================================================


```r
students2 <- read.csv("data/students_with_dates.csv")

# Preview students2 with str()
str(students2)
```

```
'data.frame':	395 obs. of  33 variables:
 $ X          : int  1 2 3 4 5 6 7 8 9 10 ...
 $ school     : chr  "GP" "GP" "GP" "GP" ...
 $ sex        : chr  "F" "F" "F" "F" ...
 $ dob        : chr  "2000-06-05" "1999-11-25" "1998-02-02" "1997-12-20" ...
 $ address    : chr  "U" "U" "U" "U" ...
 $ famsize    : chr  "GT3" "GT3" "LE3" "GT3" ...
 $ Pstatus    : chr  "A" "T" "T" "T" ...
 $ Medu       : int  4 1 1 4 3 4 2 4 3 3 ...
 $ Fedu       : int  4 1 1 2 3 3 2 4 2 4 ...
 $ Mjob       : chr  "at_home" "at_home" "at_home" "health" ...
 $ Fjob       : chr  "teacher" "other" "other" "services" ...
 $ reason     : chr  "course" "course" "other" "home" ...
 $ guardian   : chr  "mother" "father" "mother" "mother" ...
 $ traveltime : int  2 1 1 1 1 1 1 2 1 1 ...
 $ studytime  : int  2 2 2 3 2 2 2 2 2 2 ...
 $ failures   : int  0 0 3 0 0 0 0 0 0 0 ...
 $ schoolsup  : chr  "yes" "no" "yes" "no" ...
 $ famsup     : chr  "no" "yes" "no" "yes" ...
 $ paid       : chr  "no" "no" "yes" "yes" ...
 $ activities : chr  "no" "no" "no" "yes" ...
 $ nursery    : chr  "yes" "no" "yes" "yes" ...
 $ higher     : chr  "yes" "yes" "yes" "yes" ...
 $ internet   : chr  "no" "yes" "yes" "yes" ...
 $ romantic   : chr  "no" "no" "no" "yes" ...
 $ famrel     : int  4 5 4 3 4 5 4 4 4 5 ...
 $ freetime   : int  3 3 3 2 3 4 4 1 2 5 ...
 $ goout      : int  4 3 2 2 2 2 4 4 2 1 ...
 $ Dalc       : int  1 1 2 1 1 1 1 1 1 1 ...
 $ Walc       : int  1 1 3 1 2 2 1 1 1 1 ...
 $ health     : int  3 3 3 5 5 5 3 1 1 5 ...
 $ nurse_visit: chr  "2014-04-10 14:59:54" "2015-03-12 14:59:54" "2015-09-21 14:59:54" "2015-09-03 14:59:54" ...
 $ absences   : int  6 4 10 2 4 10 0 6 0 0 ...
 $ Grades     : chr  "5/6/6" "5/5/6" "7/8/10" "15/14/15" ...
```



Working with dates
========================================================


```r
# Load the lubridate package
#library(lubridate)

# Parse as date
dmy("17 Sep 2015")
```

```
[1] "2015-09-17"
```

```r
# Parse as date and time (with no seconds!)
mdy_hm("July 15, 2012 12:56")
```

```
[1] "2012-07-15 12:56:00 UTC"
```


Working with dates
========================================================


```r
# Coerce dob to a date (with no time)
students2$dob <- ymd(students2$dob)

# Coerce nurse_visit to a date and time
students2$nurse_visit <- ymd_hms(students2$nurse_visit)

# Look at students2 once more with str()
str(students2)
```

```
'data.frame':	395 obs. of  33 variables:
 $ X          : int  1 2 3 4 5 6 7 8 9 10 ...
 $ school     : chr  "GP" "GP" "GP" "GP" ...
 $ sex        : chr  "F" "F" "F" "F" ...
 $ dob        : Date, format: "2000-06-05" "1999-11-25" ...
 $ address    : chr  "U" "U" "U" "U" ...
 $ famsize    : chr  "GT3" "GT3" "LE3" "GT3" ...
 $ Pstatus    : chr  "A" "T" "T" "T" ...
 $ Medu       : int  4 1 1 4 3 4 2 4 3 3 ...
 $ Fedu       : int  4 1 1 2 3 3 2 4 2 4 ...
 $ Mjob       : chr  "at_home" "at_home" "at_home" "health" ...
 $ Fjob       : chr  "teacher" "other" "other" "services" ...
 $ reason     : chr  "course" "course" "other" "home" ...
 $ guardian   : chr  "mother" "father" "mother" "mother" ...
 $ traveltime : int  2 1 1 1 1 1 1 2 1 1 ...
 $ studytime  : int  2 2 2 3 2 2 2 2 2 2 ...
 $ failures   : int  0 0 3 0 0 0 0 0 0 0 ...
 $ schoolsup  : chr  "yes" "no" "yes" "no" ...
 $ famsup     : chr  "no" "yes" "no" "yes" ...
 $ paid       : chr  "no" "no" "yes" "yes" ...
 $ activities : chr  "no" "no" "no" "yes" ...
 $ nursery    : chr  "yes" "no" "yes" "yes" ...
 $ higher     : chr  "yes" "yes" "yes" "yes" ...
 $ internet   : chr  "no" "yes" "yes" "yes" ...
 $ romantic   : chr  "no" "no" "no" "yes" ...
 $ famrel     : int  4 5 4 3 4 5 4 4 4 5 ...
 $ freetime   : int  3 3 3 2 3 4 4 1 2 5 ...
 $ goout      : int  4 3 2 2 2 2 4 4 2 1 ...
 $ Dalc       : int  1 1 2 1 1 1 1 1 1 1 ...
 $ Walc       : int  1 1 3 1 2 2 1 1 1 1 ...
 $ health     : int  3 3 3 5 5 5 3 1 1 5 ...
 $ nurse_visit: POSIXct, format: "2014-04-10 14:59:54" "2015-03-12 14:59:54" ...
 $ absences   : int  6 4 10 2 4 10 0 6 0 0 ...
 $ Grades     : chr  "5/6/6" "5/5/6" "7/8/10" "15/14/15" ...
```


Trimming and padding strings
========================================================


```r
# Trim all leading and trailing whitespace
str_trim(c("   Filip ", "Nick  ", " Jonathan"))
```

```
[1] "Filip"    "Nick"     "Jonathan"
```


Upper and lower case
========================================================


```r
states <- c("al", "ak", "az", "ar", "ca", "co", "ct", "de", "fl", "ga", "hi", "id", "il", "in", "ia","ks", "ky", "la", "me", "md", "ma", "mi", "mn", "ms", "mo", "mt", "ne", "nv", "nh", "nj",
 "nm", "ny", "nc", "nd", "oh", "ok", "or", "pa", "ri", "sc", "sd", "tn", "tx", "ut", "vt",
 "va", "wa", "wv", "wi", "wy")

# Print state abbreviations
states
```

```
 [1] "al" "ak" "az" "ar" "ca" "co" "ct" "de" "fl" "ga" "hi" "id" "il" "in" "ia"
[16] "ks" "ky" "la" "me" "md" "ma" "mi" "mn" "ms" "mo" "mt" "ne" "nv" "nh" "nj"
[31] "nm" "ny" "nc" "nd" "oh" "ok" "or" "pa" "ri" "sc" "sd" "tn" "tx" "ut" "vt"
[46] "va" "wa" "wv" "wi" "wy"
```

Upper and lower case
========================================================


```r
# Make states all uppercase and save result to states_upper
states_upper <- toupper(states)

states_upper
```

```
 [1] "AL" "AK" "AZ" "AR" "CA" "CO" "CT" "DE" "FL" "GA" "HI" "ID" "IL" "IN" "IA"
[16] "KS" "KY" "LA" "ME" "MD" "MA" "MI" "MN" "MS" "MO" "MT" "NE" "NV" "NH" "NJ"
[31] "NM" "NY" "NC" "ND" "OH" "OK" "OR" "PA" "RI" "SC" "SD" "TN" "TX" "UT" "VT"
[46] "VA" "WA" "WV" "WI" "WY"
```



Upper and lower case
========================================================


```r
# Make states_upper all lowercase again
states_lower <- tolower(states_upper)

states_lower
```

```
 [1] "al" "ak" "az" "ar" "ca" "co" "ct" "de" "fl" "ga" "hi" "id" "il" "in" "ia"
[16] "ks" "ky" "la" "me" "md" "ma" "mi" "mn" "ms" "mo" "mt" "ne" "nv" "nh" "nj"
[31] "nm" "ny" "nc" "nd" "oh" "ok" "or" "pa" "ri" "sc" "sd" "tn" "tx" "ut" "vt"
[46] "va" "wa" "wv" "wi" "wy"
```


Finding and replacing strings
========================================================


```r
# Look at the head of students2
head(students2)
```

```
  X school sex        dob address famsize Pstatus Medu Fedu     Mjob     Fjob
1 1     GP   F 2000-06-05       U     GT3       A    4    4  at_home  teacher
2 2     GP   F 1999-11-25       U     GT3       T    1    1  at_home    other
3 3     GP   F 1998-02-02       U     LE3       T    1    1  at_home    other
4 4     GP   F 1997-12-20       U     GT3       T    4    2   health services
5 5     GP   F 1998-10-04       U     GT3       T    3    3    other    other
6 6     GP   M 1999-06-16       U     LE3       T    4    3 services    other
      reason guardian traveltime studytime failures schoolsup famsup paid
1     course   mother          2         2        0       yes     no   no
2     course   father          1         2        0        no    yes   no
3      other   mother          1         2        3       yes     no  yes
4       home   mother          1         3        0        no    yes  yes
5       home   father          1         2        0        no    yes  yes
6 reputation   mother          1         2        0        no    yes  yes
  activities nursery higher internet romantic famrel freetime goout Dalc Walc
1         no     yes    yes       no       no      4        3     4    1    1
2         no      no    yes      yes       no      5        3     3    1    1
3         no     yes    yes      yes       no      4        3     2    2    3
4        yes     yes    yes      yes      yes      3        2     2    1    1
5         no     yes    yes       no       no      4        3     2    1    2
6        yes     yes    yes      yes       no      5        4     2    1    2
  health         nurse_visit absences   Grades
1      3 2014-04-10 14:59:54        6    5/6/6
2      3 2015-03-12 14:59:54        4    5/5/6
3      3 2015-09-21 14:59:54       10   7/8/10
4      5 2015-09-03 14:59:54        2 15/14/15
5      5 2015-04-07 14:59:54        4  6/10/10
6      5 2013-11-15 14:59:54       10 15/15/15
```

```r
# Detect all dates of birth (dob) in 1997
str_detect(students2$dob, "1997")
```

```
  [1] FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE
 [13] FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE
 [25]  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
 [37]  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE
 [49]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
 [61] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE
 [73] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE
 [85] FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE  TRUE FALSE  TRUE FALSE  TRUE
 [97]  TRUE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[109] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE
[121]  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE  TRUE
[133] FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE
[145] FALSE  TRUE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE
[157] FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE  TRUE  TRUE FALSE
[169] FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
[181]  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
[193] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[205] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
[217] FALSE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE
[229] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
[241] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE
[253] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[265] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[277]  TRUE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE
[289] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE
[301] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[313] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[325] FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE
[337] FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE  TRUE
[349]  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE
[361] FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[373] FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
[385] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
```

```r
# Detect all dates of birth (dob) in 1997
str_detect(students2$dob, "1997")
```

```
  [1] FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE
 [13] FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE
 [25]  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
 [37]  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE  TRUE  TRUE
 [49]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
 [61] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE
 [73] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE
 [85] FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE  TRUE FALSE  TRUE FALSE  TRUE
 [97]  TRUE FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[109] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE
[121]  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE  TRUE
[133] FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE
[145] FALSE  TRUE FALSE FALSE  TRUE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE
[157] FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE  TRUE  TRUE FALSE
[169] FALSE FALSE FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
[181]  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE
[193] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[205] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE
[217] FALSE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE FALSE
[229] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
[241] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE
[253] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[265] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[277]  TRUE FALSE FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE FALSE FALSE
[289] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE
[301] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[313] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[325] FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE FALSE
[337] FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE  TRUE
[349]  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE
[361] FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[373] FALSE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
[385] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
```


Finding and replacing strings
========================================================


```r
# In the sex column, replace "F" with "Female"...
students2$sex <- str_replace(students2$sex, "F", "Female")

# ...And "M" with "Male"
students2$sex <- str_replace(students2$sex, "M", "Male")

head(students2)
```

```
  X school    sex        dob address famsize Pstatus Medu Fedu     Mjob
1 1     GP Female 2000-06-05       U     GT3       A    4    4  at_home
2 2     GP Female 1999-11-25       U     GT3       T    1    1  at_home
3 3     GP Female 1998-02-02       U     LE3       T    1    1  at_home
4 4     GP Female 1997-12-20       U     GT3       T    4    2   health
5 5     GP Female 1998-10-04       U     GT3       T    3    3    other
6 6     GP   Male 1999-06-16       U     LE3       T    4    3 services
      Fjob     reason guardian traveltime studytime failures schoolsup famsup
1  teacher     course   mother          2         2        0       yes     no
2    other     course   father          1         2        0        no    yes
3    other      other   mother          1         2        3       yes     no
4 services       home   mother          1         3        0        no    yes
5    other       home   father          1         2        0        no    yes
6    other reputation   mother          1         2        0        no    yes
  paid activities nursery higher internet romantic famrel freetime goout Dalc
1   no         no     yes    yes       no       no      4        3     4    1
2   no         no      no    yes      yes       no      5        3     3    1
3  yes         no     yes    yes      yes       no      4        3     2    2
4  yes        yes     yes    yes      yes      yes      3        2     2    1
5  yes         no     yes    yes       no       no      4        3     2    1
6  yes        yes     yes    yes      yes       no      5        4     2    1
  Walc health         nurse_visit absences   Grades
1    1      3 2014-04-10 14:59:54        6    5/6/6
2    1      3 2015-03-12 14:59:54        4    5/5/6
3    3      3 2015-09-21 14:59:54       10   7/8/10
4    1      5 2015-09-03 14:59:54        2 15/14/15
5    2      5 2015-04-07 14:59:54        4  6/10/10
6    2      5 2013-11-15 14:59:54       10 15/15/15
```

Finding missing values
========================================================


```r
social_df <- data.frame(name = c("Sarah", "Tom", "David", "Alice"),
                        n_friends = c(244, NA, 145, 43),
                        status = c("Going out!",  NA, "Movie night...", NA))

social_df
```

```
   name n_friends         status
1 Sarah       244     Going out!
2   Tom        NA           <NA>
3 David       145 Movie night...
4 Alice        43           <NA>
```

```r
# Call is.na() on the full social_df to spot all NAs
is.na(social_df)
```

```
      name n_friends status
[1,] FALSE     FALSE  FALSE
[2,] FALSE      TRUE   TRUE
[3,] FALSE     FALSE  FALSE
[4,] FALSE     FALSE   TRUE
```

```r
# Use the any() function to ask whether there are any NAs in the data
any(is.na(social_df))
```

```
[1] TRUE
```

```r
# View a summary() of the dataset
summary(social_df)
```

```
     name             n_friends        status         
 Length:4           Min.   : 43.0   Length:4          
 Class :character   1st Qu.: 94.0   Class :character  
 Mode  :character   Median :145.0   Mode  :character  
                    Mean   :144.0                     
                    3rd Qu.:194.5                     
                    Max.   :244.0                     
                    NA's   :1                         
```

```r
# Call table() on the status column
table(social_df$status)
```

```

    Going out! Movie night... 
             1              1 
```


Dealing with missing values
========================================================


```r
# Replace all empty strings in status with NA
social_df$status[social_df$status == ""] <- NA

# Print social_df to the console
social_df
```

```
   name n_friends         status
1 Sarah       244     Going out!
2   Tom        NA           <NA>
3 David       145 Movie night...
4 Alice        43           <NA>
```

```r
# Use complete.cases() to see which rows have no missing values
complete.cases(social_df)
```

```
[1]  TRUE FALSE  TRUE FALSE
```

```r
# Use na.omit() to remove all rows with any missing values
na.omit(social_df)
```

```
   name n_friends         status
1 Sarah       244     Going out!
3 David       145 Movie night...
```

Putting it all together
========================================================


```r
weather <- readRDS("data/weather.rds")

# Verify that weather is a data.frame
class(weather)
```

```
[1] "data.frame"
```

```r
# Check the dimensions
dim(weather)
```

```
[1] 286  35
```

```r
# View the column names
names(weather)
```

```
 [1] "X"       "year"    "month"   "measure" "X1"      "X2"      "X3"     
 [8] "X4"      "X5"      "X6"      "X7"      "X8"      "X9"      "X10"    
[15] "X11"     "X12"     "X13"     "X14"     "X15"     "X16"     "X17"    
[22] "X18"     "X19"     "X20"     "X21"     "X22"     "X23"     "X24"    
[29] "X25"     "X26"     "X27"     "X28"     "X29"     "X30"     "X31"    
```

Column names are values
========================================================


```r
# Gather the columns
weather2 <- gather(weather, day, value, X1:X31, na.rm = TRUE)

# View the head
head(weather2)
```

```
  X year month           measure day value
1 1 2014    12  Max.TemperatureF  X1    64
2 2 2014    12 Mean.TemperatureF  X1    52
3 3 2014    12  Min.TemperatureF  X1    39
4 4 2014    12    Max.Dew.PointF  X1    46
5 5 2014    12    MeanDew.PointF  X1    40
6 6 2014    12     Min.DewpointF  X1    26
```

Values are variable names
========================================================


```r
# First remove column "X" of row names
weather2 <- weather2[, -1]
head(weather2)
```

```
  year month           measure day value
1 2014    12  Max.TemperatureF  X1    64
2 2014    12 Mean.TemperatureF  X1    52
3 2014    12  Min.TemperatureF  X1    39
4 2014    12    Max.Dew.PointF  X1    46
5 2014    12    MeanDew.PointF  X1    40
6 2014    12     Min.DewpointF  X1    26
```

```r
# Spread the data
weather3 <- spread(weather2, measure, value)

# View the head
head(weather3)
```

```
  year month day CloudCover    Events Max.Dew.PointF Max.Gust.SpeedMPH
1 2014    12  X1          6      Rain             46                29
2 2014    12 X10          8      Rain             45                29
3 2014    12 X11          8 Rain-Snow             37                28
4 2014    12 X12          7      Snow             28                21
5 2014    12 X13          5                       28                23
6 2014    12 X14          4                       29                20
  Max.Humidity Max.Sea.Level.PressureIn Max.TemperatureF Max.VisibilityMiles
1           74                    30.45               64                  10
2          100                    29.58               48                  10
3           92                    29.81               39                  10
4           85                    29.88               39                  10
5           75                    29.86               42                  10
6           82                    29.91               45                  10
  Max.Wind.SpeedMPH Mean.Humidity Mean.Sea.Level.PressureIn Mean.TemperatureF
1                22            63                     30.13                52
2                23            95                      29.5                43
3                21            87                     29.61                36
4                16            75                     29.85                35
5                17            65                     29.82                37
6                15            68                     29.83                39
  Mean.VisibilityMiles Mean.Wind.SpeedMPH MeanDew.PointF Min.DewpointF
1                   10                 13             40            26
2                    3                 13             39            37
3                    7                 13             31            27
4                   10                 11             27            25
5                   10                 12             26            24
6                   10                 10             27            25
  Min.Humidity Min.Sea.Level.PressureIn Min.TemperatureF Min.VisibilityMiles
1           52                    30.01               39                  10
2           89                    29.43               38                   1
3           82                    29.44               32                   1
4           64                    29.81               31                   7
5           55                    29.78               32                  10
6           53                    29.78               33                  10
  PrecipitationIn WindDirDegrees
1            0.01            268
2            0.28            357
3            0.02            230
4               T            286
5               T            298
6            0.00            306
```

Clean up dates
========================================================


```r
# Remove X's from day column
weather3$day <- str_replace(weather3$day, "X", "")

# Unite the year, month, and day columns
weather4 <- unite(weather3, date, year, month, day, sep = "-")

# Convert date column to proper date format using lubridates's ymd()
weather4$date <- ymd(weather4$date)

# Rearrange columns using dplyr's select()
weather5 <- select(weather4, date, Events, CloudCover:WindDirDegrees)

# View the head of weather5
head(weather5)
```

```
        date    Events CloudCover Max.Dew.PointF Max.Gust.SpeedMPH Max.Humidity
1 2014-12-01      Rain          6             46                29           74
2 2014-12-10      Rain          8             45                29          100
3 2014-12-11 Rain-Snow          8             37                28           92
4 2014-12-12      Snow          7             28                21           85
5 2014-12-13                    5             28                23           75
6 2014-12-14                    4             29                20           82
  Max.Sea.Level.PressureIn Max.TemperatureF Max.VisibilityMiles
1                    30.45               64                  10
2                    29.58               48                  10
3                    29.81               39                  10
4                    29.88               39                  10
5                    29.86               42                  10
6                    29.91               45                  10
  Max.Wind.SpeedMPH Mean.Humidity Mean.Sea.Level.PressureIn Mean.TemperatureF
1                22            63                     30.13                52
2                23            95                      29.5                43
3                21            87                     29.61                36
4                16            75                     29.85                35
5                17            65                     29.82                37
6                15            68                     29.83                39
  Mean.VisibilityMiles Mean.Wind.SpeedMPH MeanDew.PointF Min.DewpointF
1                   10                 13             40            26
2                    3                 13             39            37
3                    7                 13             31            27
4                   10                 11             27            25
5                   10                 12             26            24
6                   10                 10             27            25
  Min.Humidity Min.Sea.Level.PressureIn Min.TemperatureF Min.VisibilityMiles
1           52                    30.01               39                  10
2           89                    29.43               38                   1
3           82                    29.44               32                   1
4           64                    29.81               31                   7
5           55                    29.78               32                  10
6           53                    29.78               33                  10
  PrecipitationIn WindDirDegrees
1            0.01            268
2            0.28            357
3            0.02            230
4               T            286
5               T            298
6            0.00            306
```

A closer look at column types
========================================================


```r
# Examine the data structure
glimpse(weather5)
```

```
Rows: 366
Columns: 23
$ date                      <date> 2014-12-01, 2014-12-10, 2014-12-11, 2014-12…
$ Events                    <chr> "Rain", "Rain", "Rain-Snow", "Snow", "", "",…
$ CloudCover                <chr> "6", "8", "8", "7", "5", "4", "2", "8", "8",…
$ Max.Dew.PointF            <chr> "46", "45", "37", "28", "28", "29", "33", "4…
$ Max.Gust.SpeedMPH         <chr> "29", "29", "28", "21", "23", "20", "21", "1…
$ Max.Humidity              <chr> "74", "100", "92", "85", "75", "82", "89", "…
$ Max.Sea.Level.PressureIn  <chr> "30.45", "29.58", "29.81", "29.88", "29.86",…
$ Max.TemperatureF          <chr> "64", "48", "39", "39", "42", "45", "42", "4…
$ Max.VisibilityMiles       <chr> "10", "10", "10", "10", "10", "10", "10", "1…
$ Max.Wind.SpeedMPH         <chr> "22", "23", "21", "16", "17", "15", "15", "8…
$ Mean.Humidity             <chr> "63", "95", "87", "75", "65", "68", "75", "8…
$ Mean.Sea.Level.PressureIn <chr> "30.13", "29.5", "29.61", "29.85", "29.82", …
$ Mean.TemperatureF         <chr> "52", "43", "36", "35", "37", "39", "37", "4…
$ Mean.VisibilityMiles      <chr> "10", "3", "7", "10", "10", "10", "10", "9",…
$ Mean.Wind.SpeedMPH        <chr> "13", "13", "13", "11", "12", "10", "6", "4"…
$ MeanDew.PointF            <chr> "40", "39", "31", "27", "26", "27", "29", "3…
$ Min.DewpointF             <chr> "26", "37", "27", "25", "24", "25", "27", "3…
$ Min.Humidity              <chr> "52", "89", "82", "64", "55", "53", "60", "7…
$ Min.Sea.Level.PressureIn  <chr> "30.01", "29.43", "29.44", "29.81", "29.78",…
$ Min.TemperatureF          <chr> "39", "38", "32", "31", "32", "33", "32", "3…
$ Min.VisibilityMiles       <chr> "10", "1", "1", "7", "10", "10", "10", "5", …
$ PrecipitationIn           <chr> "0.01", "0.28", "0.02", "T", "T", "0.00", "0…
$ WindDirDegrees            <chr> "268", "357", "230", "286", "298", "306", "3…
```

```r
# See what happens if we try to convert PrecipitationIn to numeric
as.numeric(weather5$PrecipitationIn)
```

```
  [1] 0.01 0.28 0.02   NA   NA 0.00 0.00   NA 0.43 0.01 0.00 0.10   NA   NA 0.05
 [16] 0.25 0.56 0.14 0.00 0.00 0.01 0.00 0.44 0.00 0.00 0.00 0.11 1.09 0.13 0.03
 [31] 2.90 0.00 0.00 0.00 0.20 0.00   NA 0.12 0.00 0.00 0.15 0.00 0.00 0.00 0.00
 [46]   NA 0.00 0.71 0.00 0.10 0.95 0.01   NA 0.62 0.06 0.05 0.57 0.00 0.02   NA
 [61] 0.00 0.01 0.00 0.05 0.01 0.03 0.00 0.23 0.39 0.00 0.02 0.01 0.06 0.78 0.00
 [76] 0.17 0.11 0.00   NA 0.07 0.02 0.00 0.00 0.00 0.00 0.09   NA 0.07 0.37 0.88
 [91] 0.17 0.06 0.01 0.00 0.00 0.80 0.27 0.00 0.14 0.00 0.00 0.01 0.05 0.09 0.00
[106] 0.00 0.00 0.04 0.80 0.21 0.12 0.00 0.26   NA 0.00 0.02   NA 0.00 0.00   NA
[121] 0.00 0.00 0.09 0.00 0.00 0.00 0.01 0.00 0.00 0.06 0.00 0.00 0.00 0.61 0.54
[136]   NA 0.00   NA 0.00 0.00 0.10 0.07 0.00 0.03 0.00 0.39 0.00 0.00 0.03 0.26
[151] 0.09 0.00 0.00 0.00 0.02 0.00 0.00 0.00   NA 0.00 0.00 0.27 0.00 0.00 0.00
[166]   NA 0.00 0.00   NA 0.00 0.00   NA 0.00 0.00 0.00 0.91 0.00 0.02 0.00 0.00
[181] 0.00 0.00 0.38 0.00 0.00 0.00   NA 0.00 0.40   NA 0.00 0.00 0.00 0.74 0.04
[196] 1.72 0.00 0.01 0.00 0.00   NA 0.20 1.43   NA 0.00 0.00 0.00   NA 0.09 0.00
[211]   NA   NA 0.50 1.12 0.00 0.00 0.00 0.03   NA 0.00   NA 0.14   NA 0.00   NA
[226]   NA 0.00 0.00 0.01 0.00   NA 0.06 0.00 0.00 0.00 0.02 0.00   NA 0.00 0.00
[241] 0.02   NA 0.15   NA 0.00 0.83 0.00 0.00 0.00 0.08 0.00 0.00 0.14 0.00 0.00
[256] 0.00 0.63   NA 0.02   NA 0.00   NA 0.00 0.00 0.00 0.00 0.00 0.00 0.49 0.00
[271] 0.00 0.00 0.00 0.00 0.00 0.17 0.66 0.01 0.38 0.00 0.00 0.00 0.00 0.00 0.00
[286] 0.00   NA 0.00 0.00 0.00 0.00 0.00 0.00 0.00 0.00 0.04 0.01 2.46   NA 0.00
[301] 0.00 0.00 0.20 0.00   NA 0.00 0.00 0.00 0.12 0.00 0.00   NA   NA   NA 0.00
[316] 0.08   NA 0.07   NA 0.00 0.00 0.03 0.00 0.00 0.36 0.73 0.01 0.00 0.00 0.00
[331] 0.00 0.00 0.00 0.00 0.34   NA 0.07 0.54 0.04 0.01 0.00 0.00 0.00 0.00 0.00
[346]   NA 0.00 0.86 0.00 0.30 0.04 0.00 0.00 0.00 0.00 0.21 0.00 0.00 0.00 0.00
[361] 0.00 0.00 0.00 0.00 0.00 0.14
```

Column type conversions
========================================================


```r
# View(weather5)

weather5$PrecipitationIn <- str_replace(weather5$PrecipitationIn, "T", "NA")

# Convert characters to numerics
weather6 <- mutate_each(weather5, funs(as.numeric), CloudCover:WindDirDegrees)

# Examine the data structure
glimpse(weather6)
```

```
Rows: 366
Columns: 23
$ date                      <date> 2014-12-01, 2014-12-10, 2014-12-11, 2014-12…
$ Events                    <chr> "Rain", "Rain", "Rain-Snow", "Snow", "", "",…
$ CloudCover                <dbl> 6, 8, 8, 7, 5, 4, 2, 8, 8, 7, 4, 7, 6, 8, 7,…
$ Max.Dew.PointF            <dbl> 46, 45, 37, 28, 28, 29, 33, 42, 46, 34, 25, …
$ Max.Gust.SpeedMPH         <dbl> 29, 29, 28, 21, 23, 20, 21, 10, 26, 30, 23, …
$ Max.Humidity              <dbl> 74, 100, 92, 85, 75, 82, 89, 96, 100, 89, 69…
$ Max.Sea.Level.PressureIn  <dbl> 30.45, 29.58, 29.81, 29.88, 29.86, 29.91, 30…
$ Max.TemperatureF          <dbl> 64, 48, 39, 39, 42, 45, 42, 44, 49, 44, 37, …
$ Max.VisibilityMiles       <dbl> 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, 10, …
$ Max.Wind.SpeedMPH         <dbl> 22, 23, 21, 16, 17, 15, 15, 8, 20, 23, 17, 2…
$ Mean.Humidity             <dbl> 63, 95, 87, 75, 65, 68, 75, 85, 85, 73, 63, …
$ Mean.Sea.Level.PressureIn <dbl> 30.13, 29.50, 29.61, 29.85, 29.82, 29.83, 30…
$ Mean.TemperatureF         <dbl> 52, 43, 36, 35, 37, 39, 37, 40, 45, 40, 33, …
$ Mean.VisibilityMiles      <dbl> 10, 3, 7, 10, 10, 10, 10, 9, 6, 10, 10, 8, 1…
$ Mean.Wind.SpeedMPH        <dbl> 13, 13, 13, 11, 12, 10, 6, 4, 11, 14, 11, 15…
$ MeanDew.PointF            <dbl> 40, 39, 31, 27, 26, 27, 29, 36, 41, 30, 22, …
$ Min.DewpointF             <dbl> 26, 37, 27, 25, 24, 25, 27, 30, 32, 26, 20, …
$ Min.Humidity              <dbl> 52, 89, 82, 64, 55, 53, 60, 73, 70, 57, 56, …
$ Min.Sea.Level.PressureIn  <dbl> 30.01, 29.43, 29.44, 29.81, 29.78, 29.78, 29…
$ Min.TemperatureF          <dbl> 39, 38, 32, 31, 32, 33, 32, 35, 41, 36, 29, …
$ Min.VisibilityMiles       <dbl> 10, 1, 1, 7, 10, 10, 10, 5, 1, 10, 10, 2, 7,…
$ PrecipitationIn           <dbl> 0.01, 0.28, 0.02, NA, NA, 0.00, 0.00, NA, 0.…
$ WindDirDegrees            <dbl> 268, 357, 230, 286, 298, 306, 324, 79, 311, …
```

Find missing values
========================================================


```r
# Count missing values
sum(is.na(weather6))
```

```
[1] 55
```

```r
# Find missing values
summary(weather6)
```

```
      date               Events            CloudCover    Max.Dew.PointF 
 Min.   :2014-12-01   Length:366         Min.   :0.000   Min.   :-6.00  
 1st Qu.:2015-03-02   Class :character   1st Qu.:3.000   1st Qu.:32.00  
 Median :2015-06-01   Mode  :character   Median :5.000   Median :47.50  
 Mean   :2015-06-01                      Mean   :4.708   Mean   :45.48  
 3rd Qu.:2015-08-31                      3rd Qu.:7.000   3rd Qu.:61.00  
 Max.   :2015-12-01                      Max.   :8.000   Max.   :75.00  
                                                                        
 Max.Gust.SpeedMPH  Max.Humidity     Max.Sea.Level.PressureIn Max.TemperatureF
 Min.   : 0.00     Min.   :  39.00   Min.   :29.58            Min.   :18.00   
 1st Qu.:21.00     1st Qu.:  73.25   1st Qu.:30.00            1st Qu.:42.00   
 Median :25.50     Median :  86.00   Median :30.14            Median :60.00   
 Mean   :26.99     Mean   :  85.69   Mean   :30.16            Mean   :58.93   
 3rd Qu.:31.25     3rd Qu.:  93.00   3rd Qu.:30.31            3rd Qu.:76.00   
 Max.   :94.00     Max.   :1000.00   Max.   :30.88            Max.   :96.00   
 NA's   :6                                                                    
 Max.VisibilityMiles Max.Wind.SpeedMPH Mean.Humidity  
 Min.   : 2.000      Min.   : 8.00     Min.   :28.00  
 1st Qu.:10.000      1st Qu.:16.00     1st Qu.:56.00  
 Median :10.000      Median :20.00     Median :66.00  
 Mean   : 9.907      Mean   :20.62     Mean   :66.02  
 3rd Qu.:10.000      3rd Qu.:24.00     3rd Qu.:76.75  
 Max.   :10.000      Max.   :38.00     Max.   :98.00  
                                                      
 Mean.Sea.Level.PressureIn Mean.TemperatureF Mean.VisibilityMiles
 Min.   :29.49             Min.   : 8.00     Min.   :-1.000      
 1st Qu.:29.87             1st Qu.:36.25     1st Qu.: 8.000      
 Median :30.03             Median :53.50     Median :10.000      
 Mean   :30.04             Mean   :51.40     Mean   : 8.861      
 3rd Qu.:30.19             3rd Qu.:68.00     3rd Qu.:10.000      
 Max.   :30.77             Max.   :84.00     Max.   :10.000      
                                                                 
 Mean.Wind.SpeedMPH MeanDew.PointF   Min.DewpointF     Min.Humidity  
 Min.   : 4.00      Min.   :-11.00   Min.   :-18.00   Min.   :16.00  
 1st Qu.: 8.00      1st Qu.: 24.00   1st Qu.: 16.25   1st Qu.:35.00  
 Median :10.00      Median : 41.00   Median : 35.00   Median :46.00  
 Mean   :10.68      Mean   : 38.96   Mean   : 32.25   Mean   :48.31  
 3rd Qu.:13.00      3rd Qu.: 56.00   3rd Qu.: 51.00   3rd Qu.:60.00  
 Max.   :22.00      Max.   : 71.00   Max.   : 68.00   Max.   :96.00  
                                                                     
 Min.Sea.Level.PressureIn Min.TemperatureF Min.VisibilityMiles PrecipitationIn 
 Min.   :29.16            Min.   :-3.00    Min.   : 0.000      Min.   :0.0000  
 1st Qu.:29.76            1st Qu.:30.00    1st Qu.: 2.000      1st Qu.:0.0000  
 Median :29.94            Median :46.00    Median :10.000      Median :0.0000  
 Mean   :29.93            Mean   :43.33    Mean   : 6.716      Mean   :0.1173  
 3rd Qu.:30.09            3rd Qu.:60.00    3rd Qu.:10.000      3rd Qu.:0.0700  
 Max.   :30.64            Max.   :74.00    Max.   :10.000      Max.   :2.9000  
                                                               NA's   :49      
 WindDirDegrees 
 Min.   :  1.0  
 1st Qu.:113.0  
 Median :222.0  
 Mean   :200.1  
 3rd Qu.:275.0  
 Max.   :360.0  
                
```


Finishing touches
========================================================


```r
new_colnames <- (c("date", "events", "cloud_cover",  "max_dew_point_f",           
                     "max_gust_speed_mph",         "max_humidity",              
                     "max_sea_level_pressure_in",  "max_temperature_f",         
                     "max_visibility_miles",       "max_wind_speed_mph",        
                     "mean_humidity",              "mean_sea_level_pressure_in",
                     "mean_temperature_f",         "mean_visibility_miles",     
                     "mean_wind_speed_mph",        "mean_dew_point_f",          
                     "min_dew_point_f",            "min_humidity",              
                     "min_sea_level_pressure_in",  "min_temperature_f",         
                     "min_visibility_miles",       "precipitation_in",          
                     "wind_dir_degrees"))

# Clean up column names
names(weather6) <- new_colnames

# Replace empty cells in events column
weather6$events[weather6$events == ""] <- "None"

# Print the first 6 rows of weather6
head(weather6)
```

```
        date    events cloud_cover max_dew_point_f max_gust_speed_mph
1 2014-12-01      Rain           6              46                 29
2 2014-12-10      Rain           8              45                 29
3 2014-12-11 Rain-Snow           8              37                 28
4 2014-12-12      Snow           7              28                 21
5 2014-12-13      None           5              28                 23
6 2014-12-14      None           4              29                 20
  max_humidity max_sea_level_pressure_in max_temperature_f max_visibility_miles
1           74                     30.45                64                   10
2          100                     29.58                48                   10
3           92                     29.81                39                   10
4           85                     29.88                39                   10
5           75                     29.86                42                   10
6           82                     29.91                45                   10
  max_wind_speed_mph mean_humidity mean_sea_level_pressure_in
1                 22            63                      30.13
2                 23            95                      29.50
3                 21            87                      29.61
4                 16            75                      29.85
5                 17            65                      29.82
6                 15            68                      29.83
  mean_temperature_f mean_visibility_miles mean_wind_speed_mph mean_dew_point_f
1                 52                    10                  13               40
2                 43                     3                  13               39
3                 36                     7                  13               31
4                 35                    10                  11               27
5                 37                    10                  12               26
6                 39                    10                  10               27
  min_dew_point_f min_humidity min_sea_level_pressure_in min_temperature_f
1              26           52                     30.01                39
2              37           89                     29.43                38
3              27           82                     29.44                32
4              25           64                     29.81                31
5              24           55                     29.78                32
6              25           53                     29.78                33
  min_visibility_miles precipitation_in wind_dir_degrees
1                   10             0.01              268
2                    1             0.28              357
3                    1             0.02              230
4                    7               NA              286
5                   10               NA              298
6                   10             0.00              306
```


Women's Football World Cup 2019 Data
========================================================

- Importing data part 1

- <https://www.fifa.com/tournaments/womens/womensworldcup/france2019>


```r
# Read in the data from the datasets folder
wwc_raw <- read_csv("data/2019_WWCFIFA_summary.csv")

# Check the dimensions and structure of the data
glimpse(wwc_raw)
```

```
Rows: 55
Columns: 13
$ Round      <chr> "Group stage", "Group stage", "Group stage", "Group stage",…
$ Wk         <chr> "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1",…
$ Day        <chr> "Fri", "Sat", "Sat", "Sat", "Sun", "Sun", "Sun", "Mon", "Mo…
$ Date       <chr> "06/07/19", "06/08/19", "06/08/19", "06/08/19", "06/09/19",…
$ Time       <time> 21:00:00, 15:00:00, 18:00:00, 21:00:00, 13:00:00, 15:30:00…
$ Home       <chr> "France", "Germany", "Spain", "Norway", "Australia", "Brazi…
$ Score      <chr> "4 - 0", "1 - 0", "3 - 1", "3 - 0", "1 - 2", "3 - 0", "2 - …
$ PKS        <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
$ Away       <chr> "Korea Rep", "China PR", "South Africa", "Nigeria", "Italy"…
$ Attendance <dbl> 45261, 15283, 12044, 11058, 15380, 17668, 13188, 25055, 107…
$ Venue      <chr> "Parc des Princes", "Roazhon Park", "Stade Oceane", "Stade …
$ Referee    <chr> "Claudia Umpierrez", "Marie-Soleil Beaudoin", "Maria Carvaj…
$ Notes      <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
```


Women's Football World Cup 2019 Data
========================================================


```r
# Check the dimensions and structure of the data
summary(wwc_raw)
```

```
    Round                Wk                Day                Date          
 Length:55          Length:55          Length:55          Length:55         
 Class :character   Class :character   Class :character   Class :character  
 Mode  :character   Mode  :character   Mode  :character   Mode  :character  
                                                                            
                                                                            
                                                                            
                                                                            
     Time              Home              Score               PKS           
 Length:55         Length:55          Length:55          Length:55         
 Class1:hms        Class :character   Class :character   Class :character  
 Class2:difftime   Mode  :character   Mode  :character   Mode  :character  
 Mode  :numeric                                                            
                                                                           
                                                                           
                                                                           
     Away             Attendance        Venue             Referee         
 Length:55          Min.   :  8009   Length:55          Length:55         
 Class :character   1st Qu.: 13476   Class :character   Class :character  
 Mode  :character   Median : 18934   Mode  :character   Mode  :character  
                    Mean   : 31777                                        
                    3rd Qu.: 22941                                        
                    Max.   :579000                                        
                    NA's   :3                                             
    Notes          
 Length:55         
 Class :character  
 Mode  :character  
                   
                   
                   
                   
```

Women's Football World Cup 2019 Data
========================================================

- Importing data part 2

Looking at the outputs, we notice a few things about the data. First, we have some NAs to address. Second, most of the columns are of type character. 


```r
# Read in the data
wwc_raw <- read_csv("data/2019_WWCFIFA_summary.csv",
                  col_types = cols(
                                  Round = col_factor(),
                                  Date = col_date(format = "%m/%d/%y"),
                                  Venue = col_factor()
                                  )
                 )
            
# Call summary() and glimpse()
glimpse(wwc_raw)
```

```
Rows: 55
Columns: 13
$ Round      <fct> Group stage, Group stage, Group stage, Group stage, Group s…
$ Wk         <chr> "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1",…
$ Day        <chr> "Fri", "Sat", "Sat", "Sat", "Sun", "Sun", "Sun", "Mon", "Mo…
$ Date       <date> 2019-06-07, 2019-06-08, 2019-06-08, 2019-06-08, 2019-06-09…
$ Time       <time> 21:00:00, 15:00:00, 18:00:00, 21:00:00, 13:00:00, 15:30:00…
$ Home       <chr> "France", "Germany", "Spain", "Norway", "Australia", "Brazi…
$ Score      <chr> "4 - 0", "1 - 0", "3 - 1", "3 - 0", "1 - 2", "3 - 0", "2 - …
$ PKS        <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
$ Away       <chr> "Korea Rep", "China PR", "South Africa", "Nigeria", "Italy"…
$ Attendance <dbl> 45261, 15283, 12044, 11058, 15380, 17668, 13188, 25055, 107…
$ Venue      <fct> Parc des Princes, Roazhon Park, Stade Oceane, Stade Auguste…
$ Referee    <chr> "Claudia Umpierrez", "Marie-Soleil Beaudoin", "Maria Carvaj…
$ Notes      <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,…
```

Women's Football World Cup 2019 Data
========================================================

- Importing data part 2

Looking at the outputs, we notice a few things about the data. First, we have some NAs to address. Second, most of the columns are of type character. 


```r
summary(wwc_raw)
```

```
             Round         Wk                Day           
 Group stage    :36   Length:55          Length:55         
                : 3   Class :character   Class :character  
 Round of 16    : 8   Mode  :character   Mode  :character  
 Quarterfinals  : 4                                        
 Semifinals     : 2                                        
 3rd-place match: 1                                        
 Final          : 1                                        
      Date                Time              Home              Score          
 Min.   :2019-06-07   Length:55         Length:55          Length:55         
 1st Qu.:2019-06-12   Class1:hms        Class :character   Class :character  
 Median :2019-06-17   Class2:difftime   Mode  :character   Mode  :character  
 Mean   :2019-06-18   Mode  :numeric                                         
 3rd Qu.:2019-06-23                                                          
 Max.   :2019-07-07                                                          
 NA's   :4                                                                   
     PKS                Away             Attendance    
 Length:55          Length:55          Min.   :  8009  
 Class :character   Class :character   1st Qu.: 13476  
 Mode  :character   Mode  :character   Median : 18934  
                                       Mean   : 31777  
                                       3rd Qu.: 22941  
                                       Max.   :579000  
                                       NA's   :3       
                      Venue      Referee             Notes          
 Parc des Princes        : 7   Length:55          Length:55         
 Roazhon Park            : 7   Class :character   Class :character  
 Stade Oceane            : 7   Mode  :character   Mode  :character  
 Stade Auguste-Delaune II: 6                                        
 Stade du Hainaut        : 6                                        
 Stade de Nice           : 6                                        
 (Other)                 :16                                        
```

Women's Football World Cup 2019 Data
========================================================

- Removing rows of NA

We have 55 observations (rows) of 13 variables (columns). Hmmm, we know there were 52 games - why the extra rows? Also Round and Attendance each have three NA, and Date and Venue each have four NA. It looks like we have a few things to fix.

- Rows of NA
- Missing data values
- Multiple values in one column (look at Score and PKS)
- Column headers are a mix of upper- and lowercase letters

The last issue is more of a preference. Having all the column names in the same case will make typing easier


```r
# Remove rows of NA
wwc_1  <- wwc_raw  %>% 
             rename_all(tolower)  %>% 
             filter(!is.na(round))

# Get the dimensions and inspect the first 10 and last 10 rows

head(wwc_1, 10)
```

```
# A tibble: 10 × 13
   round   wk    day   date       time  home  score pks   away  attendance venue
   <fct>   <chr> <chr> <date>     <tim> <chr> <chr> <chr> <chr>      <dbl> <fct>
 1 Group … 1     Fri   2019-06-07 21:00 Fran… 4 - 0 <NA>  Kore…      45261 Parc…
 2 Group … 1     Sat   2019-06-08 15:00 Germ… 1 - 0 <NA>  Chin…      15283 Roaz…
 3 Group … 1     Sat   2019-06-08 18:00 Spain 3 - 1 <NA>  Sout…      12044 Stad…
 4 Group … 1     Sat   2019-06-08 21:00 Norw… 3 - 0 <NA>  Nige…      11058 Stad…
 5 Group … 1     Sun   2019-06-09 13:00 Aust… 1 - 2 <NA>  Italy      15380 Stad…
 6 Group … 1     Sun   NA         15:30 Braz… 3 - 0 <NA>  Jama…      17668 Stad…
 7 Group … 1     Sun   2019-06-09 18:00 Engl… 2 - 1 <NA>  Scot…      13188 Stad…
 8 Group … 1     Mon   2019-06-10 18:00 Arge… 0 - 0 <NA>  Japan      25055 Parc…
 9 Group … 1     Mon   2019-06-10 21:00 Cana… 1 - 0 <NA>  Came…      10710 Stad…
10 Group … 1     Tue   2019-06-11 15:00 New … 0 - 1 <NA>  Neth…      10654 Stad…
# … with 2 more variables: referee <chr>, notes <chr>
```

Women's Football World Cup 2019 Data
========================================================

- Replacing NA

We now have 52 rows. Each row corresponds to a match in the tournament. But, it looks like there are a couple NA still lurking about in date and venue. Using colSums() and is.na() we can check to see how many NA are in each column.



```r
# Housekeeping
wwc_2 <- wwc_1

# Find and replace NA in column date
index_date <- which(is.na(wwc_2$date))

wwc_2[index_date, ]
```

```
# A tibble: 4 × 13
  round    wk    day   date   time   home   score pks   away    attendance venue
  <fct>    <chr> <chr> <date> <time> <chr>  <chr> <chr> <chr>        <dbl> <fct>
1 "Group … 1     Sun   NA     15:30  Brazil 3 - 0 <NA>  Jamaica      17668 "Sta…
2 ""       <NA>  <NA>  NA        NA  <NA>   <NA>  <NA>  <NA>            NA ""   
3 ""       <NA>  <NA>  NA        NA  <NA>   <NA>  <NA>  <NA>            NA ""   
4 ""       <NA>  <NA>  NA        NA  <NA>   <NA>  <NA>  <NA>            NA ""   
# … with 2 more variables: referee <chr>, notes <chr>
```

```r
wwc_2$date[index_date] <- "2019-06-09"

#wwc_2[index_date, ]
```

Women's Football World Cup 2019 Data
========================================================

- Replacing NA

We now have 52 rows. Each row corresponds to a match in the tournament. But, it looks like there are a couple NA still lurking about in date and venue. Using colSums() and is.na() we can check to see how many NA are in each column.



```r
# Find and replace NA in column venue
index_venue <- which(is.na(wwc_2$venue))

wwc_2[index_venue, ]
```

```
# A tibble: 0 × 13
# … with 13 variables: round <fct>, wk <chr>, day <chr>, date <date>,
#   time <time>, home <chr>, score <chr>, pks <chr>, away <chr>,
#   attendance <dbl>, venue <fct>, referee <chr>, notes <chr>
```

```r
wwc_2$venue[index_venue] <- "Groupama Stadium"

#wwc_2[index_venue, ]
```

Women's Football World Cup 2019 Data
========================================================

- separate() and replace_na()

The data are looking good, but it is a good idea to get the two data points in score and two data points in pks into their own columns for future data sleuthing.

For this task we're going to employ the functionality of separate(), mutate(), and replace_na(). 


```r
# Separate columns and replace NA
wwc_3  <- wwc_2  %>% 
  separate(score, c("home_score", "away_score"), sep =  "-", convert = TRUE)  %>% 
  separate(pks, c("home_pks", "away_pks"), sep = "-", convert = TRUE)  %>% 
  mutate(home_pks = replace_na(home_pks, 0),
         away_pks = replace_na(away_pks, 0))

# Print the data
wwc_3
```

```
# A tibble: 55 × 15
   round       wk    day   date       time  home  home_score away_score home_pks
   <fct>       <chr> <chr> <date>     <tim> <chr>      <dbl>      <int>    <dbl>
 1 Group stage 1     Fri   2019-06-07 21:00 Fran…          4          0        0
 2 Group stage 1     Sat   2019-06-08 15:00 Germ…          1          0        0
 3 Group stage 1     Sat   2019-06-08 18:00 Spain          3          1        0
 4 Group stage 1     Sat   2019-06-08 21:00 Norw…          3          0        0
 5 Group stage 1     Sun   2019-06-09 13:00 Aust…          1          2        0
 6 Group stage 1     Sun   2019-06-09 15:30 Braz…          3          0        0
 7 Group stage 1     Sun   2019-06-09 18:00 Engl…          2          1        0
 8 Group stage 1     Mon   2019-06-10 18:00 Arge…          0          0        0
 9 Group stage 1     Mon   2019-06-10 21:00 Cana…          1          0        0
10 Group stage 1     Tue   2019-06-11 15:00 New …          0          1        0
# … with 45 more rows, and 6 more variables: away_pks <int>, away <chr>,
#   attendance <dbl>, venue <fct>, referee <chr>, notes <chr>
```

Women's Football World Cup 2019 Data
========================================================

- Plotting for outliers

We corrected the NA in the date and venue columns, and separated the score and pks columns to have one score per column.

Let's plot the data to see if there are any outliers.


```r
# Housekeeping for plot size
options(repr.plot.width=8, repr.plot.height=6)

# Load package
library(ggplot2)

# Make a boxplot of attendance by venue and add the point data
ggplot(wwc_3, aes(venue, attendance)) +
  geom_boxplot() +
  geom_jitter(color = "red", size = 0.5) +
  theme(axis.text.x = element_text(angle = 90, hjust = 1))
```

![plot of chunk unnamed-chunk-50](Cleaning_data-figure/unnamed-chunk-50-1.png)

Women's Football World Cup 2019 Data
========================================================

- What to do with the outlier?

What’s up with the attendance for Groupama Stadium? One data point is almost 600,000 (6e+05) while all the other data points are less than 100,000. 

There is a mistakenly added an extra 0 in the attendance variable



```r
# Print the number of games played at each venue, and the min and max attendance at each venue
wwc_3  %>% 
  group_by(venue)  %>% 
  summarize(nb_of_games = n(), 
           min_attendance = min(attendance), 
           max_attendance = max(attendance))
```

```
# A tibble: 10 × 4
   venue                      nb_of_games min_attendance max_attendance
   <fct>                            <int>          <dbl>          <dbl>
 1 "Parc des Princes"                   7          20011          45595
 2 "Roazhon Park"                       7          13201          28267
 3 "Stade Oceane"                       7          10654          23965
 4 "Stade Auguste-Delaune II"           6          11058          19633
 5 "Stade du Hainaut"                   6          15380          22600
 6 "Stade des Alpes"                    5          11252          17988
 7 "Stade de Nice"                      6           9354          34872
 8 "Stade de la Mosson"                 5           8009          17492
 9 ""                                   4             NA             NA
10 "Groupama Stadium"                   2          48452         579000
```


Women's Football World Cup 2019 Data
========================================================



```r
# Correct the outlier
wwc_4  <- wwc_3  %>% 
  mutate(attendance = replace(attendance, which(attendance == 579000), 57900))

# Print the number of games played at each venue, and the min and max attendance at each venue
wwc_4  %>% 
  group_by(venue)  %>% 
  summarize(nb_of_games = n(), 
           min_attendance = min(attendance), 
           max_attendance = max(attendance))
```

```
# A tibble: 10 × 4
   venue                      nb_of_games min_attendance max_attendance
   <fct>                            <int>          <dbl>          <dbl>
 1 "Parc des Princes"                   7          20011          45595
 2 "Roazhon Park"                       7          13201          28267
 3 "Stade Oceane"                       7          10654          23965
 4 "Stade Auguste-Delaune II"           6          11058          19633
 5 "Stade du Hainaut"                   6          15380          22600
 6 "Stade des Alpes"                    5          11252          17988
 7 "Stade de Nice"                      6           9354          34872
 8 "Stade de la Mosson"                 5           8009          17492
 9 ""                                   4             NA             NA
10 "Groupama Stadium"                   2          48452          57900
```


Women's Football World Cup 2019 Data
========================================================

- Questions:

  - Which match had the highest attendance during the tournament?

  - In what stadium was the match with the highest attendance played?


```r
wwc_4 %>% 
  select(round, attendance, venue) %>% 
  arrange(desc(attendance))
```

```
# A tibble: 55 × 3
   round         attendance venue             
   <fct>              <dbl> <fct>             
 1 Final              57900 "Groupama Stadium"
 2 Semifinals         53512 ""                
 3 Semifinals         48452 "Groupama Stadium"
 4 Quarterfinals      45595 "Parc des Princes"
 5 Group stage        45594 "Parc des Princes"
 6 Group stage        45261 "Parc des Princes"
 7 Round of 16        38078 "Parc des Princes"
 8 Group stage        34872 "Stade de Nice"   
 9 Group stage        28267 "Roazhon Park"    
10 Group stage        28205 "Parc des Princes"
# … with 45 more rows
```

