# template elements
<div class="header"></div>
<div class="footer"></div>
<img src="../images/icjia.png" class="logo"></img>
<img src="../images/il_seal.gif" class="seal"></img>
<div class="buttons">
<a href="../index.html">
  <button type="button">Home</button>
</a>
<a href="../modules.html">
  <button type="button">Modules</button>
</a>
<a href="../notes/module3_notes1.html">
  <button type="button">Notes</button>
</a>
</div>


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 3: Data analysis with R (1)</h3>  
2018-03-28  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
<ul style="list-style: none">
<li style="color: #00061a; font-size: 1.1em; font-weight:700">
  Part 1: Getting started with tidyverse</li>
<li>
  Part 2: More on data analysis</li>
</div>


Getting Started with tidyverse
========================================================
type:section
<img src="../images/dplyr.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="20%" style="box-shadow: none; margin-left: 20%" /><img src="../images/tidyr.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="20%" style="box-shadow: none; margin-left: 20%" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.tidyverse.org/">tidyverse.org</a>
</div>


Installing the packages
========================================================
* Installing all tidyverse packages can be easily done with the follwoing command:

```r
# Install from CRAN
install.packages("tidyverse")

# Or the development version from GitHub
# install.packages("devtools")
devtools::install_github("hadley/tidyverse")
```


========================================================
* Installing `tidyverse` package installs the following:
    * core tidyverse packages
        * `ggplot2`, `dplyr`, `tidyr`, `readr`, `purrr`, `tibble`
    * packages to work with specific vector types 
        * `hms`, `stringr`, `lubridate`, `forcats`
    * packages to import data
        * `feather`, `haven`, `httr`, `jsonlite`, `readxl`, `rvest`, `xml2`
    * packages to facilitate statistical modeling
        * `modelr`, `broom`


========================================================
* Of course, each pacakge can be installed separately:

```r
# Install ggplot2
install.packages("ggplot2")

# Install both dplyr and tidyr with a single commend
#   with a character vector of the package names 
install.packages(c("dplyr", "tidyr"))
```


Importing the packages
========================================================
* Once installed, we can now import the packages using `library()`:

```r
# This imports the core tidyverse packages
library(tidyverse)

# Or import packages separately
library(dplyr)
library(tidyr)
```


Manipulating Your Data
========================================================
type:section
<img src="../images/dplyr.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.tidyverse.org/">tidyverse.org</a>
</div>


Key dplyr functions
========================================================
* `arange()`
* `select()`
* `filter()`
* `mutate()`
* `left_join()`
* `summarise()`
* `group_by()`
* `%>%`, the pipe operator


Sorting with arrange()
========================================================
**Basic format**

```r
arrange(data, column1, desc(column2), ...)
```
* A data object as the first argument
* Columns by which to sort the data as the following arguments
    * Multiple columns can be used to sort the data
    * When multiple columns are given, sorting is done hierarchically
    * Sorting in a descending order with `desc()`


========================================================
**Example**



```r
# sort by county
arrange(ispcrime, county)
```


```
  year    county violentCrime murder rape robbery aggAssault propertyCrime
1 2011     Adams          218      0   37      15        166          1555
2 2012     Adams          205      0   28      16        161          1587
3 2013     Adams          222      1   33      21        167          1564
4 2014     Adams          222      2   34      13        173          1550
5 2015     Adams          227      5   39       9        174          1268
6 2011 Alexander          119      0   14       4        101           290
  burglary larcenyTft MVTft arson
1      272       1241    36     6
2      287       1261    30     9
3      297       1204    55     8
4      305       1201    39     5
5      274        944    43     7
6       92        183    11     4
```


========================================================

```r
# sort by county and year, in a DESCENDING order
arrange(ispcrime, desc(county), desc(year))
```


```
  year    county violentCrime murder rape robbery aggAssault propertyCrime
1 2011  Woodford           15      1    4       0         10           350
2 2012  Woodford           23      0    3       1         19           405
3 2013  Woodford           17      0   10       2          5           349
4 2014  Woodford           25      0    4       0         21           283
5 2015  Woodford           29      0    5       0         24           227
6 2011 Winnebago         2430     27  150     622       1631         10569
  burglary larcenyTft MVTft arson
1       90        247    10     3
2       65        329    10     1
3       81        257    11     0
4       50        218    13     2
5       35        186     6     0
6     2635       7239   598    97
```


Filtering with filter()
========================================================
**Basic format**

```r
filter(data, condition1, condition2, ...)
```
* A data object (table) as the first argument
* Conditions by which to filter the data as the following arguments

========================================================
**Example**



Selecting with select()
========================================================
**Basic format**

```r
select(data, column1, variable2 = column2, ...)
```
* A data object (table) as the first argument
* Columns to select as the following arguments
    * Renaming each selected column is possible

========================================================
**Example**



Transforming with mutate()
========================================================
**Basic format**

```r
mutate(data, column1 = some_compuation, new_column1 = some_computation, ...)
```
* A data object (table) as the first argument
* Expressions to "mutate" columns as the following arguments
    * An exisiting column is modified with an expression with the same column name
    * A new column is created with an expression having a new column name

========================================================
**Example**


Merging with left_join()
========================================================
**Basic format**

```r
left_join(data1, data2, by = c("variables to join by"), ...)
```
* Data objects (tables) to join as the first two arguments
* A character vector of variable to join by as the third argument
* Other types of join: `inner_join()`, `right_join()`, `semi_join()`, `anti_join()`, `full_join()`


========================================================
**Example**



Aggregating with summarise()
========================================================
**Basic format**

```r
arrange(data, summary1 = some_computation, summary2 = some_computation, ...)
```
* A data object (table) as the first argument
* Expressions to summarise data as the following arguments


========================================================
**Example**



Grouping with group_by()
========================================================
**Basic format**

```r
group_by(data, column1, column2, ...)
```
* A data object as the first argument
* Columns by which to group the data as the following arguments

========================================================
**Example**



Chaining operations with %>%
========================================================
**Basic format**

```r
data %>% some_function(argument2, argument3, ...) %>% ...
```
* A data object to be manipulated comes before `%>%`
* Some function that *takes the data as the first argument* comes after `%>%`
    * The object before `%>%` is provided to the function as its first argument
* Multiple functions can be chained, or "piped"

========================================================
**Example**



dplyr in action
========================================================



More on dplyr
========================================================
* `dplyr` on [tidyverse.org](http://dplyr.tidyverse.org/)
* `dplyr` [CRAN documentation](https://cran.r-project.org/web/packages/dplyr/dplyr.pdf)
* `dplyr` [Github repository](https://github.com/tidyverse/dplyr)


Tidying Up Your Data
========================================================
type:section
<img src="../images/tidyr.png" title="plot of chunk unnamed-chunk-27" alt="plot of chunk unnamed-chunk-27" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.tidyverse.org/">tidyverse.org</a>
</div>


Key tidyr functions
========================================================
* `gather()`
* `spread()`
* `separate()`
* `extract()`
* `unite()`


Fixing "wide" data with gather()
========================================================
**Basic format**

```r
gather(data, ...)
```
* A data object as the first argument


========================================================
**Example**



Fixing "long" data with spread()
========================================================
**Basic format**

```r
spread(data, ...)
```
* A data object as the first argument


========================================================
**Example**




Splitting columns with separate()
========================================================
**Basic format**

```r
separate(data, ...)
```
* A data object as the first argument


========================================================
**Example**




Combining columns with unite()
========================================================
**Basic format**

```r
unite(data, ...)
```
* A data object as the first argument


========================================================
**Example**




Captuaring groups with extract()
========================================================
**Basic format**

```r
extract(data, ...)
```
* A data object as the first argument


========================================================
**Example**



More on tidyr
========================================================
* `tidyr` on [tidyverse.org](http://tidyr.tidyverse.org/)
* `tidyr` [CRAN documentation](https://cran.r-project.org/web/packages/tidyr/tidyr.pdf)
* `tidyr` [Github repository](https://github.com/tidyverse/tidyr)


Data manipulation with dplyr and tidyr
========================================================
**Example 1**



Questions?
========================================================
type: section
<img src="https://media.giphy.com/media/106cqwD4WrDjJm/giphy.gif" title="plot of chunk unnamed-chunk-39" alt="plot of chunk unnamed-chunk-39" width="50%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://media.giphy.com/media/106cqwD4WrDjJm/giphy.gif">giphy.com</a>
</p>


========================================================
References
<ul style="font-size: 0.6em; list-style-type:none">
  <li><a href="#">1</a></li>
  <li><a href="#">2</a></li>
  <li><a href="#">3</a></li>
  <li><a href="#"></a></li>
</ul>


========================================================
type: section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Ic_pause_circle_outline_48px.svg/2000px-Ic_pause_circle_outline_48px.svg.png" title="plot of chunk unnamed-chunk-40" alt="plot of chunk unnamed-chunk-40" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>


