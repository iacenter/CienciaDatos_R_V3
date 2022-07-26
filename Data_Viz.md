Data Visualization
========================================================
author: Alan Ponce
date: 2021-10-13 
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
- Data Visualization
- Conclusions
- Q&A

R Base: Visualization
========================================================
type: section

base package and ggplot2, part 1 - plot
========================================================


```r
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

```r
# Plot the correct variables of mtcars
plot(mtcars$wt, mtcars$mpg)
```

![plot of chunk unnamed-chunk-2](Data_Viz-figure/unnamed-chunk-2-1.png)

base package and ggplot2, part 1 - plot
========================================================


```r
str(mtcars)
```

```
'data.frame':	32 obs. of  11 variables:
 $ mpg : num  21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
 $ cyl : num  6 6 4 6 8 6 8 4 4 6 ...
 $ disp: num  160 160 108 258 360 ...
 $ hp  : num  110 110 93 110 175 105 245 62 95 123 ...
 $ drat: num  3.9 3.9 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 ...
 $ wt  : num  2.62 2.88 2.32 3.21 3.44 ...
 $ qsec: num  16.5 17 18.6 19.4 17 ...
 $ vs  : num  0 0 1 1 0 1 0 1 1 1 ...
 $ am  : num  1 1 1 0 0 0 0 0 0 0 ...
 $ gear: num  4 4 4 3 3 3 3 4 4 4 ...
 $ carb: num  4 4 1 1 2 1 4 2 2 4 ...
```

```r
# Change cyl inside mtcars to a factor
mtcars$fcyl <- as.factor(mtcars$cyl)
```

base package and ggplot2, part 1 - plot
========================================================


```r
# Make the same plot as in the first instruction but using a factor variable
plot(mtcars$wt, mtcars$mpg, col = mtcars$fcyl)
```

![plot of chunk unnamed-chunk-4](Data_Viz-figure/unnamed-chunk-4-1.png)

base package and ggplot2
========================================================


```r
plot(x = mtcars$wt, y = mtcars$mpg,
     pch = 16, frame = TRUE,
     xlab = "wt", ylab = "mpg", col = "#2E9FDF")
```

![plot of chunk unnamed-chunk-5](Data_Viz-figure/unnamed-chunk-5-1.png)



base package and ggplot2
========================================================


```r
hist(mtcars$hp)
```

![plot of chunk unnamed-chunk-6](Data_Viz-figure/unnamed-chunk-6-1.png)

base package and ggplot2
========================================================


```r
hist(mtcars$hp,,
     xlab = "Gross horsepower", 
     main = "Histogram of Motor Trend Car Road Tests",
     ylim = c(0,10))
```

![plot of chunk unnamed-chunk-7](Data_Viz-figure/unnamed-chunk-7-1.png)

base package and ggplot2
========================================================


```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

```r
pairs(iris)
```

![plot of chunk unnamed-chunk-8](Data_Viz-figure/unnamed-chunk-8-1.png)


base package and ggplot2
========================================================


```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

```r
pairs(iris, col = iris$Species)
```

![plot of chunk unnamed-chunk-9](Data_Viz-figure/unnamed-chunk-9-1.png)

base package and ggplot2
========================================================


```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

```r
plot(iris$Sepal.Length, iris$Petal.Length, col = iris$Species)
```

![plot of chunk unnamed-chunk-10](Data_Viz-figure/unnamed-chunk-10-1.png)

base package and ggplot2
========================================================


```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

```r
plot(iris$Sepal.Length, iris$Petal.Length, col = iris$Species, pch = 15)
```

![plot of chunk unnamed-chunk-11](Data_Viz-figure/unnamed-chunk-11-1.png)

base package and ggplot2
========================================================


```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

```r
plot(iris$Sepal.Length, iris$Petal.Length, col = iris$Species, pch = "A")
```

![plot of chunk unnamed-chunk-12](Data_Viz-figure/unnamed-chunk-12-1.png)

base package and ggplot2
========================================================

pch 21:25 also specify an edge colour (col) and a background colour (bg)


```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

```r
plot(iris$Sepal.Length, iris$Petal.Length, col = iris$Species, pch = 21, bg = "blue")
```

![plot of chunk unnamed-chunk-13](Data_Viz-figure/unnamed-chunk-13-1.png)

base package and ggplot2
========================================================

lets settle on solid circles (pch = 16)


```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```

```r
plot(iris$Sepal.Length, iris$Petal.Length, col = iris$Species, pch = 16)
```

![plot of chunk unnamed-chunk-14](Data_Viz-figure/unnamed-chunk-14-1.png)

base package and ggplot2
========================================================

We can change the size of the points with “cex”


```r
plot(iris$Sepal.Length, iris$Petal.Length,
     col = iris$Species,
     pch = 16,
     cex = 2)
```

![plot of chunk unnamed-chunk-15](Data_Viz-figure/unnamed-chunk-15-1.png)
base package and ggplot2
========================================================

- Barplot


```r
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6
```

```r
barplot(mtcars$cyl)
```

![plot of chunk unnamed-chunk-16](Data_Viz-figure/unnamed-chunk-16-1.png)


base package and ggplot2
========================================================

- Barplot


```r
dragons <- data.frame(
  TalonLength = c(20.9, 58.3, 35.5),
  SE = c(4.5, 6.3, 5.5),
  Population = c("England", "Scotland", "Wales"))

dragons
```

```
  TalonLength  SE Population
1        20.9 4.5    England
2        58.3 6.3   Scotland
3        35.5 5.5      Wales
```

base package and ggplot2
========================================================

- Barplot


```r
barplot(dragons$TalonLength, names = dragons$Population)
```

![plot of chunk unnamed-chunk-18](Data_Viz-figure/unnamed-chunk-18-1.png)


base package and ggplot2
========================================================

- Barplot


```r
head(VADeaths)
```

```
      Rural Male Rural Female Urban Male Urban Female
50-54       11.7          8.7       15.4          8.4
55-59       18.1         11.7       24.3         13.6
60-64       26.9         20.3       37.0         19.3
65-69       41.0         30.9       54.6         35.1
70-74       66.0         54.3       71.1         50.0
```

```r
# Subset
x <- VADeaths[1:3, "Rural Male"]
x
```

```
50-54 55-59 60-64 
 11.7  18.1  26.9 
```

```r
# Bar plot of one variable
barplot(x)
```

![plot of chunk unnamed-chunk-19](Data_Viz-figure/unnamed-chunk-19-1.png)

base package and ggplot2
========================================================

- Barplot


```r
head(x)
```

```
50-54 55-59 60-64 
 11.7  18.1  26.9 
```

```r
# Horizontal bar plot
barplot(x, horiz = TRUE)
```

![plot of chunk unnamed-chunk-20](Data_Viz-figure/unnamed-chunk-20-1.png)

base package and ggplot2
========================================================

- Barplot


```r
head(x)
```

```
50-54 55-59 60-64 
 11.7  18.1  26.9 
```

```r
# Change group names
barplot(x, names.arg = c("A", "B", "C"))
```

![plot of chunk unnamed-chunk-21](Data_Viz-figure/unnamed-chunk-21-1.png)

base package and ggplot2
========================================================

- Barplot


```r
head(x)
```

```
50-54 55-59 60-64 
 11.7  18.1  26.9 
```

```r
# Change color
# Change border and fill color using one single color
barplot(x, col = "white", border = "steelblue")
```

![plot of chunk unnamed-chunk-22](Data_Viz-figure/unnamed-chunk-22-1.png)

base package and ggplot2
========================================================

- Barplot


```r
head(x)
```

```
50-54 55-59 60-64 
 11.7  18.1  26.9 
```

```r
# Change the color of border.
#  Use different colors for each group
barplot(x, col = "white",
        border = c("#999999", "#E69F00", "#56B4E9"))
```

![plot of chunk unnamed-chunk-23](Data_Viz-figure/unnamed-chunk-23-1.png)

base package and ggplot2
========================================================

- Barplot


```r
head(x)
```

```
50-54 55-59 60-64 
 11.7  18.1  26.9 
```

```r
# Change fill color : single color
barplot(x)
```

![plot of chunk unnamed-chunk-24](Data_Viz-figure/unnamed-chunk-24-1.png)

```r
barplot(x, col = "steelblue")
```

![plot of chunk unnamed-chunk-24](Data_Viz-figure/unnamed-chunk-24-2.png)


base package and ggplot2
========================================================

- Barplot


```r
head(x)
```

```
50-54 55-59 60-64 
 11.7  18.1  26.9 
```

```r
# Change fill color: multiple colors
barplot(x, col = c("#999999", "#E69F00", "#56B4E9"))
```

![plot of chunk unnamed-chunk-25](Data_Viz-figure/unnamed-chunk-25-1.png)

base package and ggplot2
========================================================

- Barplot


```r
# Change main title and axis labels

head(x)
```

```
50-54 55-59 60-64 
 11.7  18.1  26.9 
```

```r
# Change color (col = "gray") and remove frame
barplot(x, main = "Death Rates in Virginia",
        xlab = "Age", ylab = "Rate")
```

![plot of chunk unnamed-chunk-26](Data_Viz-figure/unnamed-chunk-26-1.png)
base package and ggplot2
========================================================

- Stacked bar plots


```r
# Change main title and axis labels

head(VADeaths)
```

```
      Rural Male Rural Female Urban Male Urban Female
50-54       11.7          8.7       15.4          8.4
55-59       18.1         11.7       24.3         13.6
60-64       26.9         20.3       37.0         19.3
65-69       41.0         30.9       54.6         35.1
70-74       66.0         54.3       71.1         50.0
```

```r
barplot(VADeaths,
         col = c("lightblue", "mistyrose", "lightcyan", 
                 "lavender", "cornsilk"),
        legend = rownames(VADeaths))
```

![plot of chunk unnamed-chunk-27](Data_Viz-figure/unnamed-chunk-27-1.png)


base package and ggplot2
========================================================

- Grouped bar plots


```r
# Change main title and axis labels

head(VADeaths)
```

```
      Rural Male Rural Female Urban Male Urban Female
50-54       11.7          8.7       15.4          8.4
55-59       18.1         11.7       24.3         13.6
60-64       26.9         20.3       37.0         19.3
65-69       41.0         30.9       54.6         35.1
70-74       66.0         54.3       71.1         50.0
```

```r
barplot(VADeaths,
         col = c("lightblue", "mistyrose", "lightcyan", 
                 "lavender", "cornsilk"),
        legend = rownames(VADeaths), beside = TRUE)
```

![plot of chunk unnamed-chunk-28](Data_Viz-figure/unnamed-chunk-28-1.png)
base package and ggplot2
========================================================

- Grouped bar plots


```r
#Run all chunck code

# Define a set of colors
my_colors <- c("lightblue", "mistyrose", "lightcyan", 
                 "lavender", "cornsilk")
# Bar plot
barplot(VADeaths, col = my_colors, beside = TRUE)

# Add legend
legend("topleft", legend = rownames(VADeaths), 
       fill = my_colors, box.lty = 0, cex = 0.8
       )
```

![plot of chunk unnamed-chunk-29](Data_Viz-figure/unnamed-chunk-29-1.png)

Ggplot
========================================================
type: section

- The Grammar of Graphics

- <https://www.springer.com/gp/book/9780387245447>



Aesthetics
========================================================

Aesthetic mappings are the cornerstone of the grammar of graphics plotting concept. This is where the magic happens - converting continuous and categorical data into visual scales that provide access to a large amount of information in a very short time


```r
ggplot(iris, 
       aes(x = Sepal.Length, y = Sepal.Width)) +
        geom_point()
```

![plot of chunk unnamed-chunk-30](Data_Viz-figure/unnamed-chunk-30-1.png)



Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6
```

```r
# 1 - Map mpg to x and cyl to y
ggplot(mtcars, aes(x = mpg, y = cyl)) +
  geom_point()
```

![plot of chunk unnamed-chunk-31](Data_Viz-figure/unnamed-chunk-31-1.png)



Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6
```

```r
# 2 - Reverse: Map cyl to x and mpg to y
ggplot(mtcars, aes(x = cyl, y = mpg)) +
  geom_point()
```

![plot of chunk unnamed-chunk-32](Data_Viz-figure/unnamed-chunk-32-1.png)



Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Change cyl inside mtcars to a factor
mtcars$fcyl <- as.factor(mtcars$cyl)

# 3 - Map wt to x, mpg to y and cyl to col
ggplot(mtcars, aes(x = wt, y = mpg, col = fcyl)) +
  geom_point()
```

![plot of chunk unnamed-chunk-33](Data_Viz-figure/unnamed-chunk-33-1.png)


Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Change cyl inside mtcars to a factor
#mtcars$fcyl <- as.factor(mtcars$cyl)

# Change shape and size of the points in the above plot
ggplot(mtcars, aes(x = wt, y = mpg, col = fcyl)) +
  geom_point(shape = 1, size = 4)
```

![plot of chunk unnamed-chunk-34](Data_Viz-figure/unnamed-chunk-34-1.png)

Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# 1 - Map cyl to fill
ggplot(mtcars, aes(x = wt, y = mpg, fill = cyl)) +
  geom_point(shape = 1, size = 4)
```

![plot of chunk unnamed-chunk-35](Data_Viz-figure/unnamed-chunk-35-1.png)

Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# 2 - Change shape and alpha of the points in the above plot
ggplot(mtcars, aes(x = wt, y = mpg, fill = cyl)) +
  geom_point(shape = 21, size = 4, alpha = 0.6)
```

![plot of chunk unnamed-chunk-36](Data_Viz-figure/unnamed-chunk-36-1.png)

Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# library(RColorBrewer)

# Define a hexadecimal color
my_color <- "#4ABEFF"

# Set the color aesthetic and attribute 
ggplot(mtcars, aes(x = wt, y = mpg, color = cyl)) +
  geom_point(color = my_color)
```

![plot of chunk unnamed-chunk-37](Data_Viz-figure/unnamed-chunk-37-1.png)

Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Set the fill aesthetic and color, size and shape attributes
ggplot(mtcars, aes(x = wt, y = mpg, fill = fcyl)) +
  geom_point(size = 4, shape = 23, color = my_color)
```

![plot of chunk unnamed-chunk-38](Data_Viz-figure/unnamed-chunk-38-1.png)

Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Expand to draw points with alpha 0.5
ggplot(mtcars, aes(x = wt, y = mpg, fill = cyl)) +
  geom_point(alpha = 0.5)
```

![plot of chunk unnamed-chunk-39](Data_Viz-figure/unnamed-chunk-39-1.png)
Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Expand to draw points with shape 24 and color yellow
ggplot(mtcars, aes(x = wt, y = mpg, fill = cyl)) +
  geom_point(shape = 24, color = 'yellow')
```

![plot of chunk unnamed-chunk-40](Data_Viz-figure/unnamed-chunk-40-1.png)


Aesthetics
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Add mapping: factor(am) onto shape (now 4 aesthetics):
ggplot(mtcars, 
       aes(x = mpg, y = qsec, col = factor(cyl), shape = factor(am))) +
  geom_point()
```

![plot of chunk unnamed-chunk-41](Data_Viz-figure/unnamed-chunk-41-1.png)



Histograms
========================================================

Histograms are one of the most common and intuitive ways of showing distributions.


```r
# Print out head of mtcars
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6
```

```r
# 1 - Make a univariate histogram
ggplot(mtcars, aes(mpg)) +
  geom_histogram()
```

![plot of chunk unnamed-chunk-42](Data_Viz-figure/unnamed-chunk-42-1.png)

Histograms
========================================================

Histograms are one of the most common and intuitive ways of showing distributions.


```r
# Print out head of mtcars
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6
```

```r
# 2 - Plot 1, plus set binwidth to 1 in the geom layer
ggplot(mtcars, aes(mpg)) +
  geom_histogram(binwidth = 1)
```

![plot of chunk unnamed-chunk-43](Data_Viz-figure/unnamed-chunk-43-1.png)



Histograms
========================================================

Histograms are one of the most common and intuitive ways of showing distributions.


```r
# Print out head of mtcars
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6
```

```r
# 4 - plot 3, plus SET the fill attribute to "#377EB8"
ggplot(mtcars, aes(mpg)) +
  geom_histogram(binwidth = 1, fill = "#377EB8")
```

![plot of chunk unnamed-chunk-44](Data_Viz-figure/unnamed-chunk-44-1.png)



Bar
========================================================

geom_bar() makes the height of the bar proportional to the number of cases in each group 


```r
# Print out head of mtcars
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6
```

```r
# Change cyl inside mtcars to a factor
mtcars$fcyl <- as.factor(mtcars$cyl)

# Change cyl inside mtcars to a factor
mtcars$fam <- as.factor(mtcars$am)

# Draw a bar plot of cyl, filled according to am
ggplot(mtcars, aes(x = fcyl, fill = fam)) +
  geom_bar()
```

![plot of chunk unnamed-chunk-45](Data_Viz-figure/unnamed-chunk-45-1.png)

Bar
========================================================

dodge: place the bars next to each other.


```r
# Print out head of mtcars
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl fam
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6   1
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6   1
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4   1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6   0
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8   0
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6   0
```

```r
# Change the position argument to "dodge""
ggplot(mtcars, aes(x = fcyl, fill = fam)) +
  geom_bar(position = "dodge")
```

![plot of chunk unnamed-chunk-46](Data_Viz-figure/unnamed-chunk-46-1.png)


Bar
========================================================

Overlapping bar plots


```r
# Print out head of mtcars
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl fam
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6   1
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6   1
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4   1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6   0
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8   0
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6   0
```

```r
# 2 - Define posn_d with position_dodge()
posn_d <- position_dodge(0.2)

# 3 - Change the position argument to posn_d
ggplot(mtcars, aes(x = fcyl, fill = fam)) + 
  geom_bar(position = posn_d)
```

![plot of chunk unnamed-chunk-47](Data_Viz-figure/unnamed-chunk-47-1.png)

Bar
========================================================

Overlapping bar plots


```r
# Print out head of mtcars
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl fam
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6   1
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6   1
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4   1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6   0
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8   0
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6   0
```

```r
# 2 - Define posn_d with position_dodge()
posn_d <- position_dodge(0.2)

# 4 - Use posn_d as position and adjust alpha to 0.6
ggplot(mtcars, aes(x = fcyl, fill = fam)) + 
  geom_bar(position = posn_d, alpha = 0.6)
```

![plot of chunk unnamed-chunk-48](Data_Viz-figure/unnamed-chunk-48-1.png)

Bar
========================================================

Colors


```r
# Print out head of mtcars
head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb fcyl fam
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4    6   1
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4    6   1
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1    4   1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1    6   0
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2    8   0
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1    6   0
```

```r
# Example of how to use a brewed color palette
ggplot(mtcars, aes(x = fcyl, fill = fam)) +
  geom_bar() +
  scale_fill_brewer(palette = "Set1")
```

![plot of chunk unnamed-chunk-49](Data_Viz-figure/unnamed-chunk-49-1.png)


Line plots
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Print out head of economics
head(economics)
```

```
# A tibble: 6 × 6
  date         pce    pop psavert uempmed unemploy
  <date>     <dbl>  <dbl>   <dbl>   <dbl>    <dbl>
1 1967-07-01  507. 198712    12.6     4.5     2944
2 1967-08-01  510. 198911    12.6     4.7     2945
3 1967-09-01  516. 199113    11.9     4.6     2958
4 1967-10-01  512. 199311    12.9     4.9     3143
5 1967-11-01  517. 199498    12.8     4.7     3066
6 1967-12-01  525. 199657    11.8     4.8     3018
```

```r
# Basic line plot
ggplot(data=economics, aes(x=date, y=pop))+
  geom_line()
```

![plot of chunk unnamed-chunk-50](Data_Viz-figure/unnamed-chunk-50-1.png)

Line plots
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Print out head of economics
head(economics)
```

```
# A tibble: 6 × 6
  date         pce    pop psavert uempmed unemploy
  <date>     <dbl>  <dbl>   <dbl>   <dbl>    <dbl>
1 1967-07-01  507. 198712    12.6     4.5     2944
2 1967-08-01  510. 198911    12.6     4.7     2945
3 1967-09-01  516. 199113    11.9     4.6     2958
4 1967-10-01  512. 199311    12.9     4.9     3143
5 1967-11-01  517. 199498    12.8     4.7     3066
6 1967-12-01  525. 199657    11.8     4.8     3018
```

```r
# Plot a subset of the data
ggplot(data=subset(economics, date > as.Date("2006-1-1")), 
       aes(x=date, y=pop))+geom_line()
```

![plot of chunk unnamed-chunk-51](Data_Viz-figure/unnamed-chunk-51-1.png)


Line plots
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Print out head of economics
head(economics)
```

```
# A tibble: 6 × 6
  date         pce    pop psavert uempmed unemploy
  <date>     <dbl>  <dbl>   <dbl>   <dbl>    <dbl>
1 1967-07-01  507. 198712    12.6     4.5     2944
2 1967-08-01  510. 198911    12.6     4.7     2945
3 1967-09-01  516. 199113    11.9     4.6     2958
4 1967-10-01  512. 199311    12.9     4.9     3143
5 1967-11-01  517. 199498    12.8     4.7     3066
6 1967-12-01  525. 199657    11.8     4.8     3018
```

```r
# Plot unemploy as a function of date using a line plot
ggplot(economics, aes(x = date, y = unemploy)) +
  geom_line()
```

![plot of chunk unnamed-chunk-52](Data_Viz-figure/unnamed-chunk-52-1.png)

Line plots
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Print out head of Orange
head(Orange)
```

```
  Tree  age circumference
1    1  118            30
2    1  484            58
3    1  664            87
4    1 1004           115
5    1 1231           120
6    1 1372           142
```

```r
ggplot(Orange) +
  geom_line(aes(x = age, y = circumference, colour = Tree))
```

![plot of chunk unnamed-chunk-53](Data_Viz-figure/unnamed-chunk-53-1.png)


Line plots
========================================================

These are the aesthetics you can consider within aes() in this chapter: x, y, color, fill, size, alpha, labels and shape.


```r
# Print out head of Orange
head(Orange)
```

```
  Tree  age circumference
1    1  118            30
2    1  484            58
3    1  664            87
4    1 1004           115
5    1 1231           120
6    1 1372           142
```

```r
ggplot(Orange) +
  geom_line(aes(x = age, y = circumference, linetype = Tree))
```

![plot of chunk unnamed-chunk-54](Data_Viz-figure/unnamed-chunk-54-1.png)




