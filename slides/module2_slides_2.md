# template elements
<div class="header"></div>
<div class="footer"></div>
<img src="http://www.icjia.state.il.us/_themes/icjia/img/logo-icjia-small-blue-3.png" class="logo"></img>
<img src="https://www2.illinois.gov/PublishingImages/seal.gif" class="seal"></img>


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style.css
<h3 style="color: #789">Module 2: R basics (2)</h3>  
2018-01-01  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>  


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
  <p>Session 1: Fundamental building blocks of R programming</p>
  <p style="color: #00061a; font-size: 1.1em; font-weight:700">
    Session 2: Gearing up for data analysis in R</p>
</div>


Gearing Up for Data Analysis in R
========================================================
type:section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/66/Symbole_travaux_marteau_et_clef.svg/1080px-Symbole_travaux_marteau_et_clef.svg.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="35%" style="display: block; margin: auto; box-shadow: none;" />
  
  
R Data Frame
========================================================
type: section

```
[1] "Look, a data frame!"
```

```
  column1 column2 column3 column4 column5
1      11      12      13      14      15
2      21      22      23      24      25
3      31      32      33      34      35
4      41      42      43      44      45
5      51      52      53      54      55
```


What is a data frame?
========================================================
* A tabular representation of data where each column is a vector of some type.
    * think of Excel spreadsheets, SPSS tables, etc.!
* Can be seen as a *list of vectors* of *the same length*, but with additional functionalities for data analysis!
    * accessing data in a data frame works similarly
    * a list can be easily converted into a data frame using `as.data.frame()` (... and vice versa, with `as.list()`)


Example: Iris data 
========================================================
R comes with a data frame of [the (famous) Iris flower dataset](https://en.wikipedia.org/wiki/Iris_flower_data_set). Let's take a look:

```r
class(iris)  # the class of iris object is "data.frame"
```

```
[1] "data.frame"
```

```r
is.data.frame(iris)  # check if iris is a data.frame; TRUE, as expected
```

```
[1] TRUE
```


========================================================

```r
str(iris) # reports the "structure" of the data frame 
```

```
'data.frame':	150 obs. of  5 variables:
 $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
 $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
 $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
 $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
 $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...
```

```r
head(iris, 5)  # returns the first n rows of the data frame (default 6)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
```


========================================================

```r
dim(iris)  # returns the dimension of the data frame (row  column)
```

```
[1] 150   5
```

```r
nrow(iris)  # returns the number of rows in the data frame
```

```
[1] 150
```

```r
ncol(iris)  # returns the number of columns in the data frame
```

```
[1] 5
```

```r
colnames(iris)  # returns a vector containing the column names 
```

```
[1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width" 
[5] "Species"     
```


========================================================

```r
iris$Sepal.Length  # access a column by name
iris[[1]]          # access the first column by index
iris[, 1]          # yet another way to access the first column!
```

```
  [1] 5.1 4.9 4.7 4.6 5.0 5.4 4.6 5.0 4.4 4.9 5.4 4.8 4.8 4.3 5.8 5.7 5.4
 [18] 5.1 5.7 5.1 5.4 5.1 4.6 5.1 4.8 5.0 5.0 5.2 5.2 4.7 4.8 5.4 5.2 5.5
 [35] 4.9 5.0 5.5 4.9 4.4 5.1 5.0 4.5 4.4 5.0 5.1 4.8 5.1 4.6 5.3 5.0 7.0
 [52] 6.4 6.9 5.5 6.5 5.7 6.3 4.9 6.6 5.2 5.0 5.9 6.0 6.1 5.6 6.7 5.6 5.8
 [69] 6.2 5.6 5.9 6.1 6.3 6.1 6.4 6.6 6.8 6.7 6.0 5.7 5.5 5.5 5.8 6.0 5.4
 [86] 6.0 6.7 6.3 5.6 5.5 5.5 6.1 5.8 5.0 5.6 5.7 5.7 6.2 5.1 5.7 6.3 5.8
[103] 7.1 6.3 6.5 7.6 4.9 7.3 6.7 7.2 6.5 6.4 6.8 5.7 5.8 6.4 6.5 7.7 7.7
[120] 6.0 6.9 5.6 7.7 6.3 6.7 7.2 6.2 6.1 6.4 7.2 7.4 7.9 6.4 6.3 6.1 7.7
[137] 6.3 6.4 6.0 6.9 6.7 6.9 5.8 6.8 6.7 6.7 6.3 6.5 6.2 5.9
```

```r
iris[1, ]  # access the first row by index
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
```

```r
iris[1, 1]  # access a specific cell (first row of the first column)
```

```
[1] 5.1
```


Creating a data frame
========================================================
* Using `data.frame()`
    * with existing vectors as arguments
    * with simultanesouly creating vectors and assigning column names to them  
* Coercing a list using `as.data.frame()`


Using data.frame() 1
========================================================

```r
fruits <- c("apple", "banana", "clementine")
animals <- c("dogs", "cats", "llamas")
icecream_flavors <- c("chocolate", "vanila", "cookie dough")

df1 <- data.frame(fruits, animals, icecream_flavors)

print(df1)
```

```
      fruits animals icecream_flavors
1      apple    dogs        chocolate
2     banana    cats           vanila
3 clementine  llamas     cookie dough
```


Using data.frame() 2
========================================================

```r
df2 <- data.frame(
  fruits = c("apple", "banana", "clementine"),
  animals = c("dogs", "cats", "llamas"),
  icecream_flavors = c("chocolate", "vanila", "cookie dough")
)

print(df2)
```

```
      fruits animals icecream_flavors
1      apple    dogs        chocolate
2     banana    cats           vanila
3 clementine  llamas     cookie dough
```


Converting a list using as.data.frame()
========================================================

```r
lt <- list(
  fruits = c("apple", "banana", "clementine"),
  animals = c("dogs", "cats", "llamas"),
  icecream_flavors = c("chocolate", "vanila", "cookie dough")
)

df3 <- as.data.frame(lt)

print(df3)
```

```
      fruits animals icecream_flavors
1      apple    dogs        chocolate
2     banana    cats           vanila
3 clementine  llamas     cookie dough
```


Transforming a data frame
========================================================
* change column names
* add / modify / remove columns
* add / modify / remove rows
* modify cell values


Extending data frame
========================================================
* In practice, R's original `data.frame` is rarely used since better alternatives are available.
    * `tibble`
    * `data.table`
* Both alternatives are extension of the original `data.frame`
    * either can be manipulated just like a data frame


tibble
========================================================
* Part of the `tidyverse` framework (we'll come back to this)
* More easily understood `tidyverse` syntax
* Refined print method (showing dimension and column type information ... and more)
* Coercing a data frame into a tibble can be done with `as_tibble()` from `tibble` package 

<div style="font-size:0.75em; text-align:center">See <a href="http://r4ds.had.co.nz/tibbles.html">here</a> for more on tibble</div>


data.table
========================================================
* Made available via `data.frame` package.
* Highly optimized for larger tables (e.g. >100K rows).
* Compact syntax for advanced slicing and dicing of tablular data.
* Coercing a data frame into a data table can be done with `as.data.table()` 

<div style="font-size:0.75em; text-align:center">See <a href="https://cran.r-project.org/web/packages/data.table/vignettes/datatable-intro.html">here</a> for more on data.table</div>


R Add-On Packages
========================================================
type:section
<img src="https://s3.amazonaws.com/assets.datacamp.com/blog_assets/R+Packages+Guide/content_rdoc10.png" title="plot of chunk unnamed-chunk-12" alt="plot of chunk unnamed-chunk-12" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center">
<a href="https://www.datacamp.com/">DataCamp</a>
</div>


What are add-on packages?
========================================================
> The capabilities of R are extended through user-created packages, which allow specialized statistical techniques, graphical devices, import/export capabilities, reporting tools [...], etc. - "R (programming language)", Wikipedia


Using packages
========================================================

```r
# first we should install the desired package
install.packages("some_package")

# then we import the package to use its functionalities
library(some_package)
```


Two ways of installing packages
========================================================
* From CRAN (Comprehensive R Archive Network)
    * tested and trusted
    * using `install.packages("package")`
* From specific Github repositories (i.e., development versions)
    * latest versions with cutting-edge features 
    * using `install_github("author/package")`
        * `install_github()` is available via `devtools` package.


Tidyverse Framework
========================================================
type:section
<img src="../images/tidyverse.png" title="plot of chunk unnamed-chunk-14" alt="plot of chunk unnamed-chunk-14" width="100%" style="display: block; margin: auto; box-shadow: none;" />
<div style="font-size:0.5em; text-align:center">
<a href="https://www.tidyverse.org/">tidyverse.org</a>
</div>


Tidy approach to data science
========================================================
Tidy data is data where:
> 1. Each variable is in a column
> 2. Each observation is a row
> 3. Each value is a cell.


========================================================
<img src="http://r4ds.had.co.nz/images/tidy-1.png" title="plot of chunk unnamed-chunk-15" alt="plot of chunk unnamed-chunk-15" width="100%" style="display: block; margin-top:10%; box-shadow: none;" />
<div style="font-size:0.75em; text-align:center">See <a href="http://r4ds.had.co.nz/tidy-data.html">here</a> for more on tidy data</div>
<div style="font-size:0.5em; text-align:center">
Hadley Wickham, 2017, <a href="http://r4ds.had.co.nz/"><span style="font-style:italic">R for Data Science</span></a>
</div>


Untidy data?
========================================================
asdf


========================================================

```r
# untidy example 1
```


========================================================

```r
# untidy example 2
```


Tidyverse core packages
========================================================
* `ggplot2` for data visualization
* `dplyr` for data manipulation
* `tidyr` for creating "tidy data"
* `readr` for data import/export
* `purrr` for loop operations
* `tibble` for data representation


Good Code, Bad Code
========================================================
type:section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/8a/Ic_thumbs_up_down_48px.svg/2000px-Ic_thumbs_up_down_48px.svg.png" title="plot of chunk unnamed-chunk-18" alt="plot of chunk unnamed-chunk-18" width="40%" style="display: block; margin: auto; box-shadow: none;" />

Why style guide?
========================================================
asdf


Which style guide?
========================================================
asdf


Naming convention
========================================================
asdf


Whitespaces for readable code
========================================================
asdf


Comments for intelligible code 
========================================================
asdf

Most importantly...
========================================================
* Be consistent!
* Be concise!
* Be clear!


Questions?
========================================================
type: section
