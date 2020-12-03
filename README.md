R Markdown for GitHub
================

## Markdown vs. R Markdown

This is an R Markdown document. R Markdown uses the Markdown language,
but allows for the addition of authoring HTML, PDF, and MS Word
documents with functional code snippets and actual outputs from within
the RStudio IDE.

  - For RStudio see <https://rstudio.com/>.
  - For more details on using R Markdown see
    <http://rmarkdown.rstudio.com>.

## Converting from `README.Rmd` → `README.md`

You can clone this repository as a template for your own feature-rich
`README.md` files on GitHub.

If you open the `README.Rmd` document for editing in RStudio and click
the **Knit** button, a normal Markdown document (`README.md`) will be
generated that includes both content as well as the output of any
embedded R code chunks within the document.

## Code and output

You can embed an R code chunk like this:

``` r
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

> `cars` is one of many default example data sets in the R language.

## Images

You can also embed plots, for example:

``` r
plot(pressure)
```

![](.img/README_chunk_id_pressure-1.png)<!-- -->

> The output image from this code execution will be automatically saved
> in the `.img` subdirectory.

## Reference

  - <https://stackoverflow.com/a/39816334>

## Branch: `tutorial`

The following is an intermediate tutorial on data handling,
manipulation, processing, and reporting.

An introduction to the R language can be found here: [Introduction to
Programming (in
R)](https://github.com/atet/learn/blob/master/programming/README.md#atet--learn--programming)

### Prerequisites

  - R language and RStudio installed locally in your development
    environment:
    [Instructions](https://rstudio.com/products/rstudio/download/#download)
  - Clone this `tutorial` branch, e.g. in CLI:

<!-- end list -->

``` console
$ git clone --branch tutorial git@github.com:atet/rmd.git
```

  - Install required R packages for R Markdown support (only needs to be
    done once) and load them (needs to be done per session):

<!-- end list -->

``` r
> install.packages("knitr"); install.packages("rmarkdown"); library(knitr); library("rmarkdown")
```

  - Ensure that your working directory is at the root of this
    repository, otherwise set it using the absolute file path:
      - You can use forward slash (‘`/`’) or escaped backslashes
        (‘`\\`’) for Windows file paths

<!-- end list -->

``` r
> getwd()
[1] "<INCORRECT_FILE_PATH>"
> setwd("<CORRECT_FILE_PATH>")
```

### Background

Everything in your R environment is an object that is stored in-memory,
i.e. you can work with as large of a data set as you have RAM (*and
swap*) on your development machine.

You can quickly find information about a function by executing a ‘`?`’
in front of the function name:

``` r
> ?set.seed
```

### Loading Data

Data can be loaded directly from disk using absolute or relative paths
to current working directory:

``` r
iris1 = read.csv("./dat/iris1.csv")
iris2 = read.csv("./dat/iris2.csv")
```

..or directly from a URL:

``` r
iris3 = read.csv(url("https://raw.githubusercontent.com/atet/rmd/tutorial/dat/iris3.csv"))
iris4 = read.csv(url("https://raw.githubusercontent.com/atet/rmd/tutorial/dat/iris4.csv"))
```

### Metadata

Printing out basic object class information and number of row and
columns:

``` r
cat("The `iris1` object is of \"", class(iris1),"\" class and has ", nrow(iris1), " rows/", ncol(iris1), " columns.", sep = "")
```

    ## The `iris1` object is of "data.frame" class and has 75 rows/5 columns.

..or a summary of the object’s structure:

``` r
str(iris1)
```

    ## 'data.frame':    75 obs. of  5 variables:
    ##  $ id          : int  1 2 3 4 5 6 7 8 9 10 ...
    ##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
    ##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
    ##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
    ##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...

..or a summary of the object’s data:

``` r
summary(iris1)
```

    ##        id        Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
    ##  Min.   : 1.0   Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
    ##  1st Qu.:19.5   1st Qu.:4.900   1st Qu.:2.950   1st Qu.:1.400   1st Qu.:0.200  
    ##  Median :38.0   Median :5.100   Median :3.200   Median :1.600   Median :0.300  
    ##  Mean   :38.0   Mean   :5.341   Mean   :3.211   Mean   :2.412   Mean   :0.612  
    ##  3rd Qu.:56.5   3rd Qu.:5.700   3rd Qu.:3.500   3rd Qu.:4.000   3rd Qu.:1.250  
    ##  Max.   :75.0   Max.   :7.000   Max.   :4.400   Max.   :4.900   Max.   :1.800

..or column and row names (row names typically character numbers by
default):

``` r
colnames(iris1)
```

    ## [1] "id"           "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"

``` r
rownames(iris1)
```

    ##  [1] "1"  "2"  "3"  "4"  "5"  "6"  "7"  "8"  "9"  "10" "11" "12" "13" "14" "15"
    ## [16] "16" "17" "18" "19" "20" "21" "22" "23" "24" "25" "26" "27" "28" "29" "30"
    ## [31] "31" "32" "33" "34" "35" "36" "37" "38" "39" "40" "41" "42" "43" "44" "45"
    ## [46] "46" "47" "48" "49" "50" "51" "52" "53" "54" "55" "56" "57" "58" "59" "60"
    ## [61] "61" "62" "63" "64" "65" "66" "67" "68" "69" "70" "71" "72" "73" "74" "75"

### Subsetting

The `*.csv` files loaded are of object class `data.frame` in the current
environment. These as simple two-dimensional, tabular data sets like an
Excel spreadsheet with rows and columns.

You can reference an entire column from the `data.frame` as a vector by
using the ‘`$`’ symbol:

``` r
iris1$id
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25
    ## [26] 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50
    ## [51] 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75

..or subset rows by specifying conditions before the comma in the square
brackets below:

``` r
iris1[1, ]
```

    ##   id Sepal.Length Sepal.Width Petal.Length Petal.Width
    ## 1  1          5.1         3.5          1.4         0.2

``` r
iris1[2:3, ]
```

    ##   id Sepal.Length Sepal.Width Petal.Length Petal.Width
    ## 2  2          4.9         3.0          1.4         0.2
    ## 3  3          4.7         3.2          1.3         0.2

``` r
iris1[iris1$id == 4, ]
```

    ##   id Sepal.Length Sepal.Width Petal.Length Petal.Width
    ## 4  4          4.6         3.1          1.5         0.2

..or subset columns by specifying conditions after the comma in the
square brackets below (also subsetting rows to limit output):

> NOTE: If you subset a single column from a `data.frame`, it could be
> returned as a vector in most cases.

``` r
iris1[1:5, 1:2]
```

    ##   id Sepal.Length
    ## 1  1          5.1
    ## 2  2          4.9
    ## 3  3          4.7
    ## 4  4          4.6
    ## 5  5          5.0

``` r
iris1[1:5, c("Sepal.Width", "Petal.Length")]
```

    ##   Sepal.Width Petal.Length
    ## 1         3.5          1.4
    ## 2         3.0          1.4
    ## 3         3.2          1.3
    ## 4         3.1          1.5
    ## 5         3.6          1.4

``` r
iris1[1:5, colnames(iris1) == "Petal.Width"]
```

    ## [1] 0.2 0.2 0.2 0.2 0.2

### Manipulation

The four data sets loaded were previously split from a larger data set,
we will merge them all back together.

You can concatenate rows of data together:

``` r
iris12 = rbind(iris1, iris2)
iris34 = rbind(iris3, iris4)
```

Though you could also concatenate columns together, we will merge using
a key row `$id` to ensure that out-of-order data is merged correctly:

``` r
iris1234 = merge(iris12, iris34, by = "id")
str(iris1234)
```

    ## 'data.frame':    150 obs. of  6 variables:
    ##  $ id          : int  1 2 3 4 5 6 7 8 9 10 ...
    ##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
    ##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
    ##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
    ##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
    ##  $ Species     : chr  "setosa" "setosa" "setosa" "setosa" ...

### Summarization

Earlier we used the `summary()` function to quickly get information on
all data in a `data.frame`:

``` r
summary(iris1234)
```

    ##        id          Sepal.Length    Sepal.Width     Petal.Length  
    ##  Min.   :  1.00   Min.   :4.300   Min.   :2.000   Min.   :1.000  
    ##  1st Qu.: 38.25   1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600  
    ##  Median : 75.50   Median :5.800   Median :3.000   Median :4.350  
    ##  Mean   : 75.50   Mean   :5.843   Mean   :3.057   Mean   :3.758  
    ##  3rd Qu.:112.75   3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100  
    ##  Max.   :150.00   Max.   :7.900   Max.   :4.400   Max.   :6.900  
    ##   Petal.Width      Species         
    ##  Min.   :0.100   Length:150        
    ##  1st Qu.:0.300   Class :character  
    ##  Median :1.300   Mode  :character  
    ##  Mean   :1.199                     
    ##  3rd Qu.:1.800                     
    ##  Max.   :2.500

You can calculate the same information but for specific columns of data:

``` r
min(iris1234$Sepal.Length)
```

    ## [1] 4.3

``` r
quantile(iris1234$Sepal.Length, prob = 0.25)
```

    ## 25% 
    ## 5.1

``` r
median(iris1234$Sepal.Length)
```

    ## [1] 5.8

``` r
mean(iris1234$Sepal.Length)
```

    ## [1] 5.843333

``` r
quantile(iris1234$Sepal.Length, prob = 0.75)
```

    ## 75% 
    ## 6.4

``` r
max(iris1234$Sepal.Length)
```

    ## [1] 7.9

Additionally, you can get other descriptive statistics like variance and
standard deviation:

``` r
var(iris1234$Sepal.Length)
```

    ## [1] 0.6856935

``` r
sd(iris1234$Sepal.Length)
```

    ## [1] 0.8280661

..or all percentile bins (e.g. 25% increments):

``` r
quantile(iris1234$Sepal.Length, probs = c(0, 0.25, 0.5, 0.75, 1))
```

    ##   0%  25%  50%  75% 100% 
    ##  4.3  5.1  5.8  6.4  7.9

``` r
quantile(iris1234$Sepal.Length, probs = seq(0, 1, 0.25))
```

    ##   0%  25%  50%  75% 100% 
    ##  4.3  5.1  5.8  6.4  7.9

..or tabulating counts of unique values:

``` r
table(iris1234$Species)
```

    ## 
    ##     setosa versicolor  virginica 
    ##         50         50         50

..or binning values then tabulating the bins:

``` r
table(cut(iris1234$Sepal.Length, breaks = c(0, 4, 5, 6, 7, Inf)))
```

    ## 
    ##   (0,4]   (4,5]   (5,6]   (6,7] (7,Inf] 
    ##       0      32      57      49      12

### Visualization

Data can be quickly visualized for sanity checks or highly polished for
publication quality figures. The following are a few popular and basic
visualizations.

> NOTE: Visualizations can be saved through the RStudio GUI or
> programmatically (not shown)

#### One-Dimensional Data: Single Histogram

``` r
hist(iris1234$Sepal.Length)
```

![](.img/README_chunk_id_histogram-1.png)<!-- -->

#### One-Dimensional Data: Single Density Plot

``` r
plot(density(iris1234$Sepal.Length))
```

![](.img/README_chunk_id_density-1.png)<!-- -->

#### One-Dimensional Data: Comparative Boxplots

> NOTE: The tilde ‘`~`’ below is basically saying “..where Sepal.Length
> *depends* on Species”

``` r
boxplot(iris1234$Sepal.Length ~ iris1234$Species)
```

![](.img/README_chunk_id_boxplot-1.png)<!-- -->

#### Two-Dimensional Data: Single Scatterplot

``` r
plot(iris1234$Sepal.Length, iris1234$Sepal.Width)
```

![](.img/README_chunk_id_scatterplot1-1.png)<!-- -->

#### Two-Dimensional Data: Comparative Scatterplot

``` r
# Default, all points are black
plot(iris1234$Sepal.Length, iris1234$Sepal.Width)
# Subset out Setosa and add blue points
points(iris1234[iris1234$Species == "setosa",]$Sepal.Length, iris1234[iris1234$Species == "setosa",]$Sepal.Width, col = "blue")
# Subset out Versicolor and red points
points(iris1234[iris1234$Species == "versicolor",]$Sepal.Length, iris1234[iris1234$Species == "versicolor",]$Sepal.Width, col = "red")
```

![](.img/README_chunk_id_scatterplot2-1.png)<!-- -->

### Output

The `data.frame` objects can be saved back to disk as a `*.csv` (or any
other delimiter):

``` r
write.csv(iris1234, "./dat/iris1234.csv", row.names = FALSE)
```

..or as an `*.rds` R object (default is compressed).

``` r
saveRDS(iris1234, "./dat/iris1234.rds", compress = TRUE)
```

### Protips

The R language works natively on vectors, therefore there are large
performance gains leveraging this functionality compared to looping over
data structures:

``` r
set.seed(1)
vc = rnorm(100000000)
system.time({
  result1 = 0
  for(i in 1:length(vc)){
    result1 = result1 + vc[i]
  }
})[3]
```

    ## elapsed 
    ##    3.74

``` r
system.time({
  result2 = sum(vc)
})[3]
```

    ## elapsed 
    ##    0.12

``` r
all.equal(result1, result2)
```

    ## [1] TRUE

TODO: Multi-threading

<center>

Copyright © 2020-∞
<a href="http://www.athitkao.com" target="_blank">Athit Kao,
<a href="http://www.athitkao.com/tos.html" target="_blank">Terms and
Conditions</a>

</center>
