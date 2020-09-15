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

![](.img/README_unnamed-chunk-2-1.png)<!-- -->

> The output image from this code execution will be automatically saved
> in the `.img` subdirectory.

## Reference

  - <https://stackoverflow.com/a/39816334>
