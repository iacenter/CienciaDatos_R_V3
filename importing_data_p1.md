Importing data
========================================================
author:Alán Ponce
date: 2022-07-12 
autosize: true 


<div align="center">
<img src="imgs/ia_center.jpeg" width=700 height=600>
</div>




Agenda
========================================================
type: section

- Quick recap
  - R Data Structures
  - Tidyyverse
- Importing data
  - read.csv
  - read.delim
  - read.table
  - read_csv
  - fread
  - Excel files
  - Import flat files from the web
  - JavaScript Object Notation (JSON)
- Conclusions
- Q&A

Quick recap
========================================================
type: section
<div align="center">
<img src="imgs/ds_R.png" width=700 height=500>
</div>

<!-- ![title](imgs/ds_R.png) -->

Tidyverse
========================================================
type: section

- The pipe operator %>% 
- Filter
- Arrange
- Mutate 
- summarize
  - mean
  - sum
  - median
  - min
  - max
- Group by (group_by)
- ggplot2
  
Quick recap: Code
======================================================== 


```r
gapminder %>%
    group_by(year, continent) %>% 
    summarize(totalPop = sum(pop),
    meanLifeExp = mean(lifeExp))
```

```
# A tibble: 60 × 4
# Groups:   year [12]
    year continent   totalPop meanLifeExp
   <int> <fct>          <dbl>       <dbl>
 1  1952 Africa     237640501        39.1
 2  1952 Americas   345152446        53.3
 3  1952 Asia      1395357351        46.3
 4  1952 Europe     418120846        64.4
 5  1952 Oceania     10686006        69.3
 6  1957 Africa     264837738        41.3
 7  1957 Americas   386953916        56.0
 8  1957 Asia      1562780599        49.3
 9  1957 Europe     437890351        66.7
10  1957 Oceania     11941976        70.3
# … with 50 more rows
```

Quick recap: Viz
======================================================== 

![plot of chunk unnamed-chunk-3](importing_data_p1-figure/unnamed-chunk-3-1.png)


Importing data:
========================================================
type: section

- read.csv
- read.delim
- read.table
- read_csv
- fread
- vroom



read.csv
========================================================

- The utils package, which is automatically loaded in your R session on startup, can import CSV files with the read.csv() function.


```r
# Import swimming_pools.csv: pools
pools <- read.csv("data/swimming_pools.csv")

# Print the structure of pools
str(pools)
```

```
'data.frame':	20 obs. of  4 variables:
 $ Name     : chr  "Acacia Ridge Leisure Centre" "Bellbowrie Pool" "Carole Park" "Centenary Pool (inner City)" ...
 $ Address  : chr  "1391 Beaudesert Road, Acacia Ridge" "Sugarwood Street, Bellbowrie" "Cnr Boundary Road and Waterford Road Wacol" "400 Gregory Terrace, Spring Hill" ...
 $ Latitude : num  -27.6 -27.6 -27.6 -27.5 -27.4 ...
 $ Longitude: num  153 153 153 153 153 ...
```

read.csv
========================================================

- With **stringsAsFactors**, you can tell R whether it should convert strings in the flat file to factors.

- For all importing functions in the utils package, this argument is TRUE, which means that you import strings as factors. This only makes sense if the strings you import represent categorical variables in R. If you set stringsAsFactors to FALSE, the data frame columns corresponding to strings in your text file will be character.


```r
# Import gapminder data
data("gapminder")

str(gapminder)
```

```
tibble [1,704 × 6] (S3: tbl_df/tbl/data.frame)
 $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
 $ year     : int [1:1704] 1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
 $ lifeExp  : num [1:1704] 28.8 30.3 32 34 36.1 ...
 $ pop      : int [1:1704] 8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
 $ gdpPercap: num [1:1704] 779 821 853 836 740 ...
```

read.csv
========================================================

- The utils package, which is automatically loaded in your R session on startup, can import CSV files with the read.csv() function.



```r
gapminder_2 <- read.csv("data/gapminder_2.csv", stringsAsFactors = FALSE)

# Check the structure of pools
str(gapminder_2)
```

```
'data.frame':	1704 obs. of  7 variables:
 $ X        : int  1 2 3 4 5 6 7 8 9 10 ...
 $ country  : chr  "Afghanistan" "Afghanistan" "Afghanistan" "Afghanistan" ...
 $ continent: chr  "Asia" "Asia" "Asia" "Asia" ...
 $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
 $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
 $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
 $ gdpPercap: num  779 821 853 836 740 ...
```

read.delim
========================================================

- Aside from .csv files, there are also the .txt files which are basically text files. You can import these functions with read.delim(). 

- By default, it sets the sep argument to "\t" (fields in a record are delimited by tabs) and the header argument to TRUE (the first row contains the field names).



```r
# Import hotdogs.txt: hotdogs
hotdogs <- read.delim("data/hotdogs.txt", header = FALSE)
#hotdogs

# Summarize hotdogs
str(hotdogs)
```

```
'data.frame':	54 obs. of  3 variables:
 $ V1: chr  "Beef" "Beef" "Beef" "Beef" ...
 $ V2: int  186 181 176 149 184 190 158 139 175 148 ...
 $ V3: int  495 477 425 322 482 587 370 322 479 375 ...
```


read.delim
========================================================

- By default, it sets the sep argument to "\t" (fields in a record are delimited by tabs) and the header argument to TRUE (the first row contains the field names).



```r
# Import hotdogs.txt: hotdogs
hotdogs <- read.delim("data/hotdogs.txt",  sep = "\t", 
                      col.names = c("type", "calories", "sodium"))

# Call head() on hotdogs
head(hotdogs)
```

```
  type calories sodium
1 Beef      181    477
2 Beef      176    425
3 Beef      149    322
4 Beef      184    482
5 Beef      190    587
6 Beef      158    370
```

read.table
========================================================

- It's the most basic importing function; you can specify tons of different arguments in this function.


```r
# Path to the hotdogs.txt file: path
path <- file.path("data", "hotdogs.txt")

# Import the hotdogs.txt file: hotdogs
hotdogs <- read.table(path, 
                      sep = "\t", 
                      col.names = c("type", "calories", "sodium"))

# Call head() on hotdogs
head(hotdogs)
```

```
  type calories sodium
1 Beef      186    495
2 Beef      181    477
3 Beef      176    425
4 Beef      149    322
5 Beef      184    482
6 Beef      190    587
```

Column classes
========================================================

- You can also specify the column types or column classes of the resulting data frame


```r
# Edit the colClasses argument to import the data correctly: hotdogs2
hotdogs2 <- read.delim("data/hotdogs.txt", 
                       header = FALSE, 
                       col.names = c("type", "calories", "sodium"),
                       colClasses = c("factor", "NULL", "numeric")
                       )

# Display structure of hotdogs2
str(hotdogs2)
```

```
'data.frame':	54 obs. of  2 variables:
 $ type  : Factor w/ 3 levels "Beef","Meat",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ sodium: num  495 477 425 322 482 587 370 322 479 375 ...
```

read_csv
========================================================
type: section

read_csv
========================================================

- CSV files can be imported with read_csv(). It's a wrapper function around read_delim() that handles all the details for you.


```r
# Load the readr package
#library(readr)

# Import potatoes.csv with read_csv(): potatoes
potatoes <- read_csv("data/potatoes.csv")

head(potatoes)
```

```
# A tibble: 6 × 8
   area  temp  size storage method texture flavor moistness
  <dbl> <dbl> <dbl>   <dbl>  <dbl>   <dbl>  <dbl>     <dbl>
1     1     1     1       1      1     2.9    3.2       3  
2     1     1     1       1      2     2.3    2.5       2.6
3     1     1     1       1      3     2.5    2.8       2.8
4     1     1     1       1      4     2.1    2.9       2.4
5     1     1     1       1      5     1.9    2.8       2.2
6     1     1     1       2      1     1.8    3         1.7
```

read_tsv
========================================================

- Where you use read_csv() to easily read in CSV files, you use read_tsv() to easily read in TSV files. TSV is short for tab-separated values.


```r
# Column names
properties <- c("area", "temp", "size", "storage", "method",
                "texture", "flavor", "moistness")

# Import potatoes.txt: potatoes
potatoes <- read_tsv("data/potatoes.txt", col_names = properties) %>% 
  glimpse() %>% 
  View()
```

```
Rows: 161
Columns: 8
$ area      <chr> "area", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1…
$ temp      <chr> "temp", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1…
$ size      <chr> "size", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1…
$ storage   <chr> "storage", "1", "1", "1", "1", "1", "2", "2", "2", "2", "2",…
$ method    <chr> "method", "1", "2", "3", "4", "5", "1", "2", "3", "4", "5", …
$ texture   <chr> "texture", "2.9", "2.3", "2.5", "2.1", "1.9", "1.8", "2.6", …
$ flavor    <chr> "flavor", "3.2", "2.5", "2.8", "2.9", "2.8", "3.0", "3.1", "…
$ moistness <chr> "moistness", "3.0", "2.6", "2.8", "2.4", "2.2", "1.7", "2.4"…
```

```r
# Call head() on potatoes
head(potatoes)
```

```
NULL
```

read_tsv
========================================================

- You'll again be working potatoes.txt; the file uses tabs ("\t") to delimit values and does not contain column names in its first line.


```r
# Column names
properties <- c("area", "temp", "size", "storage", "method",
                "texture", "flavor", "moistness")

# Import potatoes.txt using read_delim(): potatoes
potatoes <- read_delim("data/potatoes2.txt", 
                       delim = "\t", 
                       col_names = properties) %>% glimpse() 
```

```
Rows: 160
Columns: 8
$ area      <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
$ temp      <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
$ size      <dbl> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, …
$ storage   <dbl> 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 3, 3, 3, 3, 3, 4, 4, 4, 4, 4, …
$ method    <dbl> 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, …
$ texture   <dbl> 2.9, 2.3, 2.5, 2.1, 1.9, 1.8, 2.6, 3.0, 2.2, 2.0, 1.8, 2.0, …
$ flavor    <dbl> 3.2, 2.5, 2.8, 2.9, 2.8, 3.0, 3.1, 3.0, 3.2, 2.8, 2.6, 2.8, …
$ moistness <dbl> 3.0, 2.6, 2.8, 2.4, 2.2, 1.7, 2.4, 2.9, 2.5, 1.9, 1.5, 1.9, …
```

```r
# Print out potatoes
potatoes
```

```
# A tibble: 160 × 8
    area  temp  size storage method texture flavor moistness
   <dbl> <dbl> <dbl>   <dbl>  <dbl>   <dbl>  <dbl>     <dbl>
 1     1     1     1       1      1     2.9    3.2       3  
 2     1     1     1       1      2     2.3    2.5       2.6
 3     1     1     1       1      3     2.5    2.8       2.8
 4     1     1     1       1      4     2.1    2.9       2.4
 5     1     1     1       1      5     1.9    2.8       2.2
 6     1     1     1       2      1     1.8    3         1.7
 7     1     1     1       2      2     2.6    3.1       2.4
 8     1     1     1       2      3     3      3         2.9
 9     1     1     1       2      4     2.2    3.2       2.5
10     1     1     1       2      5     2      2.8       1.9
# … with 150 more rows
```

skip and n_max
========================================================

Through skip and n_max you can control which part of your flat file you're actually importing into R.

- skip specifies the number of lines you're ignoring in the flat file before actually starting to import data.

- n_max specifies the number of lines you're actually importing.


```r
# Column names
properties <- c("area", "temp", "size", "storage", "method",
                "texture", "flavor", "moistness")

# Import 5 observations from potatoes.txt: potatoes_fragment
potatoes_fragment <- read_tsv("data/potatoes.txt", 
                              skip = 6, n_max = 15, 
                              col_names = properties) 

#potatoes_fragment <- read_tsv("data/potatoes.txt", skip = 6, n_max = 5)

head(potatoes_fragment)
```

```
# A tibble: 6 × 8
   area  temp  size storage method texture flavor moistness
  <dbl> <dbl> <dbl>   <dbl>  <dbl>   <dbl>  <dbl>     <dbl>
1     1     1     1       2      1     1.8    3         1.7
2     1     1     1       2      2     2.6    3.1       2.4
3     1     1     1       2      3     3      3         2.9
4     1     1     1       2      4     2.2    3.2       2.5
5     1     1     1       2      5     2      2.8       1.9
6     1     1     1       3      1     1.8    2.6       1.5
```


col_types
========================================================

- You can also specify which types the columns in your imported data frame should have


```r
# Column names
properties <- c("area", "temp", "size", "storage", "method",
                "texture", "flavor", "moistness")

# Import all data, but force all columns to be character: potatoes_char
potatoes_char <- read_tsv("data/potatoes2.txt", 
                          col_types = "cccccccc", 
                          col_names = properties) %>% glimpse()
```

```
Rows: 160
Columns: 8
$ area      <chr> "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", …
$ temp      <chr> "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", …
$ size      <chr> "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", …
$ storage   <chr> "1", "1", "1", "1", "1", "2", "2", "2", "2", "2", "3", "3", …
$ method    <chr> "1", "2", "3", "4", "5", "1", "2", "3", "4", "5", "1", "2", …
$ texture   <chr> "2.9", "2.3", "2.5", "2.1", "1.9", "1.8", "2.6", "3.0", "2.2…
$ flavor    <chr> "3.2", "2.5", "2.8", "2.9", "2.8", "3.0", "3.1", "3.0", "3.2…
$ moistness <chr> "3.0", "2.6", "2.8", "2.4", "2.2", "1.7", "2.4", "2.9", "2.5…
```

```r
# Print out structure of potatoes_char
str(potatoes_char)
```

```
spec_tbl_df [160 × 8] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
 $ area     : chr [1:160] "1" "1" "1" "1" ...
 $ temp     : chr [1:160] "1" "1" "1" "1" ...
 $ size     : chr [1:160] "1" "1" "1" "1" ...
 $ storage  : chr [1:160] "1" "1" "1" "1" ...
 $ method   : chr [1:160] "1" "2" "3" "4" ...
 $ texture  : chr [1:160] "2.9" "2.3" "2.5" "2.1" ...
 $ flavor   : chr [1:160] "3.2" "2.5" "2.8" "2.9" ...
 $ moistness: chr [1:160] "3.0" "2.6" "2.8" "2.4" ...
 - attr(*, "spec")=
  .. cols(
  ..   area = col_character(),
  ..   temp = col_character(),
  ..   size = col_character(),
  ..   storage = col_character(),
  ..   method = col_character(),
  ..   texture = col_character(),
  ..   flavor = col_character(),
  ..   moistness = col_character()
  .. )
 - attr(*, "problems")=<externalptr> 
```

col_types with collectors:
========================================================

- Another way of setting the types of the imported columns is using collectors. 

- Collector functions can be passed in a list() to the col_types argument of read_ functions to tell them how to interpret values in a column.


```r
# The collectors you will need to import the data
fac <- col_factor(levels = c("Beef", "Meat", "Poultry"))
int <- col_integer()

# Edit the col_types argument to import the data correctly: hotdogs_factor
hotdogs_factor <- read_tsv("data/hotdogs.txt",
                           col_names = c("type", "calories", "sodium"),
                           col_types = list(fac, int, int)) %>% glimpse()
```

```
Rows: 54
Columns: 3
$ type     <fct> Beef, Beef, Beef, Beef, Beef, Beef, Beef, Beef, Beef, Beef, B…
$ calories <int> 186, 181, 176, 149, 184, 190, 158, 139, 175, 148, 152, 111, 1…
$ sodium   <int> 495, 477, 425, 322, 482, 587, 370, 322, 479, 375, 330, 300, 3…
```

```r
# Display the summary of hotdogs_factor
head(hotdogs_factor)
```

```
# A tibble: 6 × 3
  type  calories sodium
  <fct>    <int>  <int>
1 Beef       186    495
2 Beef       181    477
3 Beef       176    425
4 Beef       149    322
5 Beef       184    482
6 Beef       190    587
```

fread
========================================================
type: section

fread
========================================================

- Fast and friendly file finagler

- You still remember how to use read.table(), right? Well, fread() is a function that does the same job with very similar arguments


```r
# load the data.table package
#library(data.table)

# Import potatoes.csv with fread(): potatoes
potatoes <- fread("data/potatoes.csv")

# Print out potatoes
potatoes
```

```
     area temp size storage method texture flavor moistness
  1:    1    1    1       1      1     2.9    3.2       3.0
  2:    1    1    1       1      2     2.3    2.5       2.6
  3:    1    1    1       1      3     2.5    2.8       2.8
  4:    1    1    1       1      4     2.1    2.9       2.4
  5:    1    1    1       1      5     1.9    2.8       2.2
 ---                                                       
156:    2    2    2       4      1     2.7    3.3       2.6
157:    2    2    2       4      2     2.6    2.8       2.3
158:    2    2    2       4      3     2.5    3.1       2.6
159:    2    2    2       4      4     3.4    3.3       3.0
160:    2    2    2       4      5     2.5    2.8       2.3
```

fread
========================================================

- Now that you know the basics about fread(), you should know about two arguments of the function: drop and select, to drop or select variables of interest.


```r
# Import columns 6 and 8 of potatoes.csv: potatoes
potatoes <- fread("data/potatoes.csv", select = c(6, 8))

head(potatoes)
```

```
   texture moistness
1:     2.9       3.0
2:     2.3       2.6
3:     2.5       2.8
4:     2.1       2.4
5:     1.9       2.2
6:     1.8       1.7
```

```r
# Plot texture (x) and moistness (y) of potatoes
plot(potatoes$texture, potatoes$moistness)
```

![plot of chunk unnamed-chunk-18](importing_data_p1-figure/unnamed-chunk-18-1.png)

vroom
========================================================


```r
#library(vroom)

potatoes <- vroom("data/potatoes.csv")
```


Conclusions
========================================================
type: section

- read.csv
- read.delim
- read.table
- read_csv
- fread
- vroom

Q&A
========================================================





