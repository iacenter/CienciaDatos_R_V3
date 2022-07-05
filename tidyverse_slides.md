<style>
.reveal h1, .reveal h2, .reveal h3 {
  word-wrap: normal;
  -moz-hyphens: none;
}
.small-code pre code {
  font-size: 1em;
}
.midcenter {
    position: fixed;
    top: 50%;
    left: 50%;
}
.footer {
    color: black; background: #E8E8E8;
    position: fixed; top: 90%;
    text-align:center; width:100%;
}
.pinky .reveal .state-background {
  background: #FF69B4;
} 
.pinky .reveal h1,
.pinky .reveal h2,
.pinky .reveal p {
  color: black;
}
</style>

Tidyverse
========================================================
author:Alán Ponce
date: 2021-09-22 
autosize: true 


<div align="center">
<img src="imgs/ia_center.jpeg" width=700 height=600>
</div>

<!-- ![title](imgs/ia_center.jpeg) -->


Agenda
========================================================

- Quick recap
- RStudio Server
- Subsetting 
- Introduction to Tidyyverse (1)
  - Grammatical verbs
- Packages and libraries
  - Gapminder
- Tidyverse: Data Wrangling
- Conclusions
- Q&A

Subsetting (slicing)
========================================================
type: section

<div align="center">
<img src="imgs/subset.png" width=500 height=400>
</div>

Slicing
========================================================
class: small-code
- The process of selecting specific rows and columns of data based on some criteria.



```r
#mtcars

head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```

Slicing (1)
========================================================
class: small-code

Use the notation **data[rows, columns]**, where rows and columns are vectors of integers.


```r
# Return row 1
mtcars[1,]
```

```
          mpg cyl disp  hp drat   wt  qsec vs am gear carb
Mazda RX4  21   6  160 110  3.9 2.62 16.46  0  1    4    4
```

Slicing (2)
========================================================
class: small-code

Use the notation **data[rows, columns]**, where rows and columns are vectors of integers.


```r
# Return column 4

mtcars[, 4]
```

```
 [1] 110 110  93 110 175 105 245  62  95 123 123 180 180 180 205 215 230  66  52
[20]  65  97 150 150 245 175  66  91 113 264 175 335 109
```

```r
#head(mtcars[, 4])
```

Slicing (3)
========================================================
Use the notation **data[rows, columns]**, where rows and columns are vectors of integers.


```r
#head(mtcars)

# Rows 1:5 and column 2
mtcars[1:5, 2]
```

```
[1] 6 6 4 6 8
```

Slicing (4)
========================================================
Use the notation **data[rows, columns]**, where rows and columns are vectors of integers.


```r
# Give me the rows 1-5 and column 1 of mtcars
mtcars[1:5, 1]
```

```
[1] 21.0 21.0 22.8 21.4 18.7
```

Slicing (5)
========================================================
Use the notation **data[rows, columns]**, where rows and columns are vectors of integers.



```r
# Give me rows 1-3 and columns 1 and 3 of mtcars
mtcars[1:3, c(1,3)]
```

```
               mpg disp
Mazda RX4     21.0  160
Mazda RX4 Wag 21.0  160
Datsun 710    22.8  108
```

**R indexing start from 1 not zero**

**[start:end]**

**inclusive:exclusive**

Slicing (6)
========================================================
class: small-code

Use the notation **data[rows, columns]**, where rows and columns are vectors of integers.


```r
# Give me the 3nd column (and all rows) of mtcars
mtcars[, 3]
```

```
 [1] 160.0 160.0 108.0 258.0 360.0 225.0 360.0 146.7 140.8 167.6 167.6 275.8
[13] 275.8 275.8 472.0 460.0 440.0  78.7  75.7  71.1 120.1 318.0 304.0 350.0
[25] 400.0  79.0 120.3  95.1 351.0 145.0 301.0 121.0
```

Slicing (7)
========================================================
Use the notation **data[rows, columns]**, where rows and columns are vectors of integers.


```r
#  where cyl equals 4
mtcars[mtcars$cyl == 4, ]
```

```
                mpg cyl  disp  hp drat    wt  qsec vs am gear carb
Datsun 710     22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
Merc 240D      24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
Merc 230       22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
Fiat 128       32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
Honda Civic    30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
Toyota Corolla 33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
Toyota Corona  21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
Fiat X1-9      27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
Porsche 914-2  26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
Lotus Europa   30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
Volvo 142E     21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2
```

Slicing (7)
========================================================
Use the notation **data[rows, columns]**, where rows and columns are vectors of integers.


```r
#  where cyl equals 4 and hp > 108
mtcars[mtcars$cyl == 4 & mtcars$hp > 108, ]
```

```
              mpg cyl  disp  hp drat    wt qsec vs am gear carb
Lotus Europa 30.4   4  95.1 113 3.77 1.513 16.9  1  1    5    2
Volvo 142E   21.4   4 121.0 109 4.11 2.780 18.6  1  1    4    2
```

Slicing with subset()
========================================================
It allows you to slice and dice datasets just like you would with brackets, but the code is much easier to write

Arguments

- x	object to be subsetted.
- subset logical expression indicating elements or rows to keep: missing values are taken as false.
- select expression, indicating columns to select from a data frame.


```r
# Get rows of mtcars where cyl equals 4 and hp > 108
subset(x = mtcars, 
       subset = cyl == 4  & hp >  108 |  hp < 190)
```

```
                   mpg cyl  disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
Merc 240D         24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
Merc 230          22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
Merc 280          19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
Merc 280C         17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
Merc 450SE        16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
Merc 450SL        17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
Merc 450SLC       15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
Fiat 128          32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
Honda Civic       30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
Toyota Corolla    33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
Toyota Corona     21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
Dodge Challenger  15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
AMC Javelin       15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
Pontiac Firebird  19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
Fiat X1-9         27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
Porsche 914-2     26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
Lotus Europa      30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
Ferrari Dino      19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
Volvo 142E        21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2
```

Slicing with subset()
========================================================
It allows you to slice and dice datasets just like you would with brackets, but the code is much easier to write



```r
# Get rows of mtcars where cyl equals 4 and hp > 108 but only return the wt and am columns
subset(x = mtcars, 
       subset = cyl == 4  & hp <  108,
       select = c(wt, am))
```

```
                  wt am
Datsun 710     2.320  1
Merc 240D      3.190  0
Merc 230       3.150  0
Fiat 128       2.200  1
Honda Civic    1.615  1
Toyota Corolla 1.835  1
Toyota Corona  2.465  0
Fiat X1-9      1.935  1
Porsche 914-2  2.140  1
```



Tidyverse
========================================================
type: section

<div align="center">
<img src="imgs/tidyverse.jpeg" width=450 height=350>
</div>


<div style="text-align: right"> 

https://www.tidyverse.org/

</div>


Tidyverse
========================================================
type: sub-section

<div align="center">
<img src="imgs/tidyverse2.jpeg" width=450 height=350>
</div>



Tidyverse
========================================================

Official site, please visit <https://www.tidyverse.org/>.

- R Base
  - loops
- What is Tidyverse?
  - Tidy paper <https://www.jstatsoft.org/article/view/v059i10>
- Grammatical verbs
- Community and dissemination



Packages and libraries
========================================================
- R packages extend the functionality of R by providing additional functions, data, and documentation. 

- They are written by a worldwide community of R users and can be downloaded for free from the interne


```r
#-- Install a package
# install.packages("tidyverse")

#-- Install several packages
# install.packages(c("tidyverse", "gapminder", "ggmap", "ggplot2")) # rest omitted

#-- Load a library
library(tidyverse)
library(gapminder)
```

- Cran site, please visit <https://cran.r-project.org/web/packages/gapminder/README.html>.

- Official site, please visit <https://www.gapminder.org/about/about-gapminder/history/>.


Gapminder
========================================================

- Excerpt of the Gapminder data on life expectancy, GDP per capita, and population by country.


```r
head(gapminder)
```

```
# A tibble: 6 × 6
  country     continent  year lifeExp      pop gdpPercap
  <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
1 Afghanistan Asia       1952    28.8  8425333      779.
2 Afghanistan Asia       1957    30.3  9240934      821.
3 Afghanistan Asia       1962    32.0 10267083      853.
4 Afghanistan Asia       1967    34.0 11537966      836.
5 Afghanistan Asia       1972    36.1 13079460      740.
6 Afghanistan Asia       1977    38.4 14880372      786.
```

Tidyverse: Data Wrangling
========================================================
type: sub-section


The pipe operator: 
========================================================
- dplyr package

- The pipe operator allows us to combine multiple operations in R into a single sequential chain of actions.


<div align="center">
<img src="imgs/pipe_operator.jpeg" width=450 height=350>
</div>

Tidyverse: Filter
========================================================
type: sub-section


Filter
========================================================

- It allows you to specify criteria about the values of a variable in your dataset and then filters out only the rows that match that criteria.


```r
gapminder %>% filter(year == 2007)
```

```
# A tibble: 142 × 6
   country     continent  year lifeExp       pop gdpPercap
   <fct>       <fct>     <int>   <dbl>     <int>     <dbl>
 1 Afghanistan Asia       2007    43.8  31889923      975.
 2 Albania     Europe     2007    76.4   3600523     5937.
 3 Algeria     Africa     2007    72.3  33333216     6223.
 4 Angola      Africa     2007    42.7  12420476     4797.
 5 Argentina   Americas   2007    75.3  40301927    12779.
 6 Australia   Oceania    2007    81.2  20434176    34435.
 7 Austria     Europe     2007    79.8   8199783    36126.
 8 Bahrain     Asia       2007    75.6    708573    29796.
 9 Bangladesh  Asia       2007    64.1 150448339     1391.
10 Belgium     Europe     2007    79.4  10392226    33693.
# … with 132 more rows
```
Filter
========================================================


```r
gapminder %>%
  filter(country == "United States")
```

```
# A tibble: 12 × 6
   country       continent  year lifeExp       pop gdpPercap
   <fct>         <fct>     <int>   <dbl>     <int>     <dbl>
 1 United States Americas   1952    68.4 157553000    13990.
 2 United States Americas   1957    69.5 171984000    14847.
 3 United States Americas   1962    70.2 186538000    16173.
 4 United States Americas   1967    70.8 198712000    19530.
 5 United States Americas   1972    71.3 209896000    21806.
 6 United States Americas   1977    73.4 220239000    24073.
 7 United States Americas   1982    74.6 232187835    25010.
 8 United States Americas   1987    75.0 242803533    29884.
 9 United States Americas   1992    76.1 256894189    32004.
10 United States Americas   1997    76.8 272911760    35767.
11 United States Americas   2002    77.3 287675526    39097.
12 United States Americas   2007    78.2 301139947    42952.
```


Filter
========================================================


```r
gapminder %>%
  filter(year == 2007, country == "United States")
```

```
# A tibble: 1 × 6
  country       continent  year lifeExp       pop gdpPercap
  <fct>         <fct>     <int>   <dbl>     <int>     <dbl>
1 United States Americas   2007    78.2 301139947    42952.
```

Tidyverse: Arrange
========================================================
type: sub-section

Arrange
========================================================

- It sorts a table based on a variable


```r
gapminder %>% arrange(gdpPercap)
```

```
# A tibble: 1,704 × 6
   country          continent  year lifeExp      pop gdpPercap
   <fct>            <fct>     <int>   <dbl>    <int>     <dbl>
 1 Congo, Dem. Rep. Africa     2002    45.0 55379852      241.
 2 Congo, Dem. Rep. Africa     2007    46.5 64606759      278.
 3 Lesotho          Africa     1952    42.1   748747      299.
 4 Guinea-Bissau    Africa     1952    32.5   580653      300.
 5 Congo, Dem. Rep. Africa     1997    42.6 47798986      312.
 6 Eritrea          Africa     1952    35.9  1438760      329.
 7 Myanmar          Asia       1952    36.3 20092996      331 
 8 Lesotho          Africa     1957    45.0   813338      336.
 9 Burundi          Africa     1952    39.0  2445618      339.
10 Eritrea          Africa     1957    38.0  1542611      344.
# … with 1,694 more rows
```

Arrange
========================================================

- It sorts a table based on a variable: Sorting in descending order


```r
gapminder %>% arrange(desc(gdpPercap))
```

```
# A tibble: 1,704 × 6
   country   continent  year lifeExp     pop gdpPercap
   <fct>     <fct>     <int>   <dbl>   <int>     <dbl>
 1 Kuwait    Asia       1957    58.0  212846   113523.
 2 Kuwait    Asia       1972    67.7  841934   109348.
 3 Kuwait    Asia       1952    55.6  160000   108382.
 4 Kuwait    Asia       1962    60.5  358266    95458.
 5 Kuwait    Asia       1967    64.6  575003    80895.
 6 Kuwait    Asia       1977    69.3 1140357    59265.
 7 Norway    Europe     2007    80.2 4627926    49357.
 8 Kuwait    Asia       2007    77.6 2505559    47307.
 9 Singapore Asia       2007    80.0 4553009    47143.
10 Norway    Europe     2002    79.0 4535591    44684.
# … with 1,694 more rows
```


Filtering then arranging
========================================================


```r
gapminder %>%
  filter(year == 2007) %>% arrange(desc(gdpPercap))
```

```
# A tibble: 142 × 6
   country          continent  year lifeExp       pop gdpPercap
   <fct>            <fct>     <int>   <dbl>     <int>     <dbl>
 1 Norway           Europe     2007    80.2   4627926    49357.
 2 Kuwait           Asia       2007    77.6   2505559    47307.
 3 Singapore        Asia       2007    80.0   4553009    47143.
 4 United States    Americas   2007    78.2 301139947    42952.
 5 Ireland          Europe     2007    78.9   4109086    40676.
 6 Hong Kong, China Asia       2007    82.2   6980412    39725.
 7 Switzerland      Europe     2007    81.7   7554661    37506.
 8 Netherlands      Europe     2007    79.8  16570613    36798.
 9 Canada           Americas   2007    80.7  33390141    36319.
10 Iceland          Europe     2007    81.8    301931    36181.
# … with 132 more rows
```

Tidyverse: Mutate
========================================================
type: sub-section


Mutate
========================================================
- Using mutate to change a variable


```r
gapminder %>%
  mutate(pop = pop / 1000000)
```

```
# A tibble: 1,704 × 6
   country     continent  year lifeExp   pop gdpPercap
   <fct>       <fct>     <int>   <dbl> <dbl>     <dbl>
 1 Afghanistan Asia       1952    28.8  8.43      779.
 2 Afghanistan Asia       1957    30.3  9.24      821.
 3 Afghanistan Asia       1962    32.0 10.3       853.
 4 Afghanistan Asia       1967    34.0 11.5       836.
 5 Afghanistan Asia       1972    36.1 13.1       740.
 6 Afghanistan Asia       1977    38.4 14.9       786.
 7 Afghanistan Asia       1982    39.9 12.9       978.
 8 Afghanistan Asia       1987    40.8 13.9       852.
 9 Afghanistan Asia       1992    41.7 16.3       649.
10 Afghanistan Asia       1997    41.8 22.2       635.
# … with 1,694 more rows
```

Mutate
========================================================
- Using mutate to add a new variable


```r
gapminder %>%
  mutate(gdp = gdpPercap * pop)
```

```
# A tibble: 1,704 × 7
   country     continent  year lifeExp      pop gdpPercap          gdp
   <fct>       <fct>     <int>   <dbl>    <int>     <dbl>        <dbl>
 1 Afghanistan Asia       1952    28.8  8425333      779.  6567086330.
 2 Afghanistan Asia       1957    30.3  9240934      821.  7585448670.
 3 Afghanistan Asia       1962    32.0 10267083      853.  8758855797.
 4 Afghanistan Asia       1967    34.0 11537966      836.  9648014150.
 5 Afghanistan Asia       1972    36.1 13079460      740.  9678553274.
 6 Afghanistan Asia       1977    38.4 14880372      786. 11697659231.
 7 Afghanistan Asia       1982    39.9 12881816      978. 12598563401.
 8 Afghanistan Asia       1987    40.8 13867957      852. 11820990309.
 9 Afghanistan Asia       1992    41.7 16317921      649. 10595901589.
10 Afghanistan Asia       1997    41.8 22227415      635. 14121995875.
# … with 1,694 more rows
```
Combining verbs
========================================================
- mutate, filter, arrange


```r
gapminder %>%
  mutate(gdp = gdpPercap * pop) %>% filter(year == 2007) %>% arrange(desc(gdp))
```

```
# A tibble: 142 × 7
   country        continent  year lifeExp        pop gdpPercap     gdp
   <fct>          <fct>     <int>   <dbl>      <int>     <dbl>   <dbl>
 1 United States  Americas   2007    78.2  301139947    42952. 1.29e13
 2 China          Asia       2007    73.0 1318683096     4959. 6.54e12
 3 Japan          Asia       2007    82.6  127467972    31656. 4.04e12
 4 India          Asia       2007    64.7 1110396331     2452. 2.72e12
 5 Germany        Europe     2007    79.4   82400996    32170. 2.65e12
 6 United Kingdom Europe     2007    79.4   60776238    33203. 2.02e12
 7 France         Europe     2007    80.7   61083916    30470. 1.86e12
 8 Brazil         Americas   2007    72.4  190010647     9066. 1.72e12
 9 Italy          Europe     2007    80.5   58147733    28570. 1.66e12
10 Mexico         Americas   2007    76.2  108700891    11978. 1.30e12
# … with 132 more rows
```

The summarize verb
========================================================

- Functions you can use for summarizing
    - mean
    - sum
    - median
    - min
    - max


```r
gapminder %>%
  summarize(meanLifeExp = mean(lifeExp))
```

```
# A tibble: 1 × 1
  meanLifeExp
        <dbl>
1        59.5
```

The summarize verb
========================================================
 -Summarizing one year


```r
gapminder %>%
  filter(year == 2007) %>% summarize(meanLifeExp = mean(lifeExp))
```

```
# A tibble: 1 × 1
  meanLifeExp
        <dbl>
1        67.0
```


The summarize verb
========================================================
 -Summarizing one year


```r
gapminder %>%
  filter(year == 2007) %>% 
  summarize(meanLifeExp = mean(lifeExp), totalPop = sum(pop))
```

```
# A tibble: 1 × 2
  meanLifeExp   totalPop
        <dbl>      <dbl>
1        67.0 6251013179
```

The group_by verb
======================================================== 

- Summarizing by year


```r
gapminder %>%
  group_by(year) %>% 
  summarize(meanLifeExp = mean(lifeExp), totalPop = sum(pop))
```

```
# A tibble: 12 × 3
    year meanLifeExp   totalPop
   <int>       <dbl>      <dbl>
 1  1952        49.1 2406957150
 2  1957        51.5 2664404580
 3  1962        53.6 2899782974
 4  1967        55.7 3217478384
 5  1972        57.6 3576977158
 6  1977        59.6 3930045807
 7  1982        61.5 4289436840
 8  1987        63.2 4691477418
 9  1992        64.2 5110710260
10  1997        65.0 5515204472
11  2002        65.7 5886977579
12  2007        67.0 6251013179
```
The group_by verb
======================================================== 

- Summarizing by continent


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

Visualizing with ggplot2
======================================================== 

- <https://ggplot2.tidyverse.org/>
- Summarizing by continent



```r
library(ggplot2)

gapminder_2007 <- gapminder %>% filter(year == 2007)

gapminder_2007
```

```
# A tibble: 142 × 6
   country     continent  year lifeExp       pop gdpPercap
   <fct>       <fct>     <int>   <dbl>     <int>     <dbl>
 1 Afghanistan Asia       2007    43.8  31889923      975.
 2 Albania     Europe     2007    76.4   3600523     5937.
 3 Algeria     Africa     2007    72.3  33333216     6223.
 4 Angola      Africa     2007    42.7  12420476     4797.
 5 Argentina   Americas   2007    75.3  40301927    12779.
 6 Australia   Oceania    2007    81.2  20434176    34435.
 7 Austria     Europe     2007    79.8   8199783    36126.
 8 Bahrain     Asia       2007    75.6    708573    29796.
 9 Bangladesh  Asia       2007    64.1 150448339     1391.
10 Belgium     Europe     2007    79.4  10392226    33693.
# … with 132 more rows
```

Visualizing with ggplot2
======================================================== 

- Summarizing by continent


```r
ggplot(gapminder_2007, 
       aes(x = gdpPercap, y = lifeExp)) + 
          geom_point()
```

<img src="tidyverse_slides-figure/unnamed-chunk-29-1.png" title="plot of chunk unnamed-chunk-29" alt="plot of chunk unnamed-chunk-29" style="display: block; margin: auto;" />


Visualizing with ggplot2
======================================================== 

- Summarizing by continent


```r
ggplot(gapminder_2007, 
       aes(x = gdpPercap, y = lifeExp)) + 
          geom_point() + scale_x_log10()
```

<img src="tidyverse_slides-figure/unnamed-chunk-30-1.png" title="plot of chunk unnamed-chunk-30" alt="plot of chunk unnamed-chunk-30" style="display: block; margin: auto;" />


Visualizing with ggplot2
======================================================== 

- The color aesthetic


```r
ggplot(gapminder_2007, 
       aes(x = gdpPercap, y = lifeExp, color = continent)) + 
          geom_point() + scale_x_log10()
```

<img src="tidyverse_slides-figure/unnamed-chunk-31-1.png" title="plot of chunk unnamed-chunk-31" alt="plot of chunk unnamed-chunk-31" style="display: block; margin: auto;" />


Visualizing with ggplot2
======================================================== 

- The size aesthestic


```r
ggplot(gapminder_2007, 
       aes(x = gdpPercap, y = lifeExp, color = continent, size = pop)) + 
          geom_point() + scale_x_log10()
```

<img src="tidyverse_slides-figure/unnamed-chunk-32-1.png" title="plot of chunk unnamed-chunk-32" alt="plot of chunk unnamed-chunk-32" style="display: block; margin: auto;" />

Visualizing with ggplot2
======================================================== 

- Faceting


```r
ggplot(gapminder_2007, 
       aes(x = gdpPercap, y = lifeExp, color = continent, size = pop)) + 
          geom_point() + scale_x_log10() +
            facet_wrap(~ continent)
```

<img src="tidyverse_slides-figure/unnamed-chunk-33-1.png" title="plot of chunk unnamed-chunk-33" alt="plot of chunk unnamed-chunk-33" style="display: block; margin: auto;" />

Reading files
======================================================== 

- Reading files




```
processing file: tidyverse_slides.Rpres
── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
✓ ggplot2 3.3.5     ✓ purrr   0.3.4
✓ tibble  3.1.3     ✓ dplyr   1.0.7
✓ tidyr   1.1.3     ✓ stringr 1.4.0
✓ readr   2.0.1     ✓ forcats 0.5.1
── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
x dplyr::filter() masks stats::filter()
x dplyr::lag()    masks stats::lag()
`summarise()` has grouped output by 'year'. You can override using the `.groups` argument.
Quitting from lines 589-594 (tidyverse_slides.Rpres) 
Error: 'data/gapminder.csv' does not exist in current working directory ('/Volumes/GoogleDrive/My Drive/PhD/Software/R/Code/DS_R_TA').
Execution halted
```
