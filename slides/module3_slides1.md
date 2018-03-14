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
<link href="https://fonts.googleapis.com/css?family=Oswald" rel="stylesheet">


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
<br>
* `arange()`
* `select()` `rename()`
* `filter()`
* `mutate()` `trasmute()`

***
<br>
* `left_join()`
* `summarise()`
* `group_by()` `ungroup()`
* `%>%`, the pipe operator


Sort rows by variables
========================================================

```r
arrange(tbl, ...)
```
* The first argument is a tabular data object
    * e.g. `data.frame` or `tibble`
* Columns by which to sort the data as other arguments
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


Filter rows with conditions
========================================================

```r
filter(tbl, ...)
```
* The first argument is a tabular data object
* The following arguments are conditional expressions
    * Only the rows satisfying the given conditions are kept  

========================================================
**Example**

```r
ispcrime %>%
  filter(
    year == 2015,
    murder > 0
  ) %>%
  head()
```

```
  year    county violentCrime murder rape robbery aggAssault propertyCrime
1 2015     Adams          227      5   39       9        174          1268
2 2015      Bond            5      1    0       0          4           130
3 2015    Bureau           53      1   17       4         31           360
4 2015 Champaign          918      7  127     205        579          5568
5 2015     Coles          173      1   33      14        125           632
6 2015      Cook        28791    534 1911   11217      15129        124784
  burglary larcenyTft MVTft arson
1      274        944    43     7
2       39         84     7     0
3      110        244     6     0
4     1100       4235   196    37
5      146        463    13    10
6    20550      90675 12547  1012
```


Select and/or rename variables
========================================================

```r
select(tbl, ...)
rename(tbl, ...)
```
* The first argument is a tabular data object 
* The following arguments are columns to select/rename
    * `select()` returns the selected columns only while `rename()` keeps all columns
    * Renaming each selected column is also possible with `select()`
* `select()` can be also used to exclude a section of columns using a minus (`-`) sign while keeping the rest.


========================================================
**Example**

```r
# select with renaming columns
ispcrime %>%
  select(year, county, v_crime = violentCrime, p_crime = propertyCrime) %>%
  head()
```

```
  year    county v_crime p_crime
1 2011     Adams     218    1555
2 2011 Alexander     119     290
3 2011      Bond       6     211
4 2011     Boone      59     733
5 2011     Brown       7      38
6 2011    Bureau      42     505
```


========================================================

```r
# excluding columns
ispcrime %>%
  select(-violentCrime, -propertyCrime) %>%
  head()
```

```
  year    county murder rape robbery aggAssault burglary larcenyTft MVTft
1 2011     Adams      0   37      15        166      272       1241    36
2 2011 Alexander      0   14       4        101       92        183    11
3 2011      Bond      1    0       0          5       58        147     5
4 2011     Boone      0   24       8         27      152        563    14
5 2011     Brown      0    1       0          6       14         22     1
6 2011    Bureau      0    4       3         35       90        405     8
  arson
1     6
2     4
3     1
4     4
5     1
6     2
```


Transform and add variables
========================================================

```r
transmute(tbl, ...)
mutate(tbl, ...)
```
* The first argument is a tabular data object 
* The following arguments transform or add columns
    * An exisiting column is modified with an expression with the same column name
    * A new column is created with an expression having a new column name
    * `transmute()` returns the transformed/added columns only while `mutate()` keeps all columns

========================================================
**Example**

```r
ispcrime %>%
  mutate(totalCrime = violentCrime + propertyCrime) %>%
  head()
```

```
  year    county violentCrime murder rape robbery aggAssault propertyCrime
1 2011     Adams          218      0   37      15        166          1555
2 2011 Alexander          119      0   14       4        101           290
3 2011      Bond            6      1    0       0          5           211
4 2011     Boone           59      0   24       8         27           733
5 2011     Brown            7      0    1       0          6            38
6 2011    Bureau           42      0    4       3         35           505
  burglary larcenyTft MVTft arson totalCrime
1      272       1241    36     6       1773
2       92        183    11     4        409
3       58        147     5     1        217
4      152        563    14     4        792
5       14         22     1     1         45
6       90        405     8     2        547
```

Merge tables
========================================================

```r
left_join(tbl1, tbl2, by = NULL, ...)
```
* The first two arguments are tabular data objects to join 
* `by` takes a chracter vector containing a selection of variables to join tables by
    * By default, all columns with common names are used
* Other types of join: `inner_join()`, `right_join()`, `semi_join()`, `anti_join()`, `full_join()`


========================================================
**Venn diagrams for join types**

<img src="../images/join-venn.png" title="plot of chunk unnamed-chunk-20" alt="plot of chunk unnamed-chunk-20" width="100%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: Wickham, H. (2017). <a href="http://r4ds.had.co.nz/relational-data.html"><span href="font-style:italic">R for Data Science</span></a>
</div>


========================================================
**Example**

```r
ispcrime %>%
  left_join(regions, by = "county") %>%
  head()
```

```
  year    county violentCrime murder rape robbery aggAssault propertyCrime
1 2011     Adams          218      0   37      15        166          1555
2 2011 Alexander          119      0   14       4        101           290
3 2011      Bond            6      1    0       0          5           211
4 2011     Boone           59      0   24       8         27           733
5 2011     Brown            7      0    1       0          6            38
6 2011    Bureau           42      0    4       3         35           505
  burglary larcenyTft MVTft arson   region
1      272       1241    36     6  Central
2       92        183    11     4 Southern
3       58        147     5     1 Southern
4      152        563    14     4 Northern
5       14         22     1     1  Central
6       90        405     8     2  Central
```


Aggregate and summarise rows
========================================================

```r
summarise(tbl, ...)
summarize(tbl, ...)
```
* The first argument is a tabular data object
* The following arguments are expressions to summarise data
    * `summarise()` and `summarize()` are identical
    * each summary column resulting from each summarizing expression can be given a name


========================================================
**Example**

```r
ispcrime %>%
  summarise(
    violentCrimeAverage = mean(violentCrime, na.rm = TRUE),
    propertyCrimeAverage = mean(propertyCrime, na.rm = TRUE)
  )
```

```
  violentCrimeAverage propertyCrimeAverage
1            500.9702             2912.905
```


Group by variables
========================================================

```r
group_by(tbl, ...)
ungroup(tbl, ...)
```
* The first argument is a tabular data object
* The following arguments are columns by which to group the data
  * `group_by()` and `ungroup()` are the opposite operations
* `group_by()` can be used in combination with other function to allow for group-specific data manipulations


========================================================
**Example**

```r
ispcrime %>%
  group_by(year)
```

```
# A tibble: 510 x 12
# Groups:   year [5]
    year county violentCrime murder  rape robbery aggAssault propertyCrime
   <int> <fct>         <int>  <int> <int>   <int>      <int>         <int>
 1  2011 Adams           218      0    37      15        166          1555
 2  2011 Alexa~          119      0    14       4        101           290
 3  2011 Bond              6      1     0       0          5           211
 4  2011 Boone            59      0    24       8         27           733
 5  2011 Brown             7      0     1       0          6            38
 6  2011 Bureau           42      0     4       3         35           505
 7  2011 Calho~           13      0     0       0         13            56
 8  2011 Carro~            8      0     1       0          7           206
 9  2011 Cass             12      0     1       0         11           119
10  2011 Champ~         1210      5   127     208        870          5332
# ... with 500 more rows, and 4 more variables: burglary <int>,
#   larcenyTft <int>, MVTft <int>, arson <int>
```


========================================================

```r
ispcrime %>%
  group_by(year) %>%
  summarise(
    violentCrimeAverage = mean(violentCrime, na.rm = TRUE),
    propertyCrimeAverage = mean(propertyCrime, na.rm = TRUE)
  )
```

```
# A tibble: 5 x 3
   year violentCrimeAverage propertyCrimeAverage
  <int>               <dbl>                <dbl>
1  2011                 538                 3329
2  2012                 520                 3192
3  2013                 503                 2940
4  2014                 464                 2609
5  2015                 478                 2481
```


Chain operations
========================================================

```r
data %>% function1(arg2, ...) %>% ...
```
* A data object to be manipulated comes before `%>%`
* Some function that *takes the data as the first argument* comes after `%>%`
    * The object before `%>%` is provided to the function as its first argument
* Multiple functions can be chained, or "piped"


========================================================
**Comparison**

```r
# piping style
object %>%
  function1(arguments1) %>%
  function2(arguments2) %>%
  function3(arguments3)


# traditional style
function3(
  function2(
    function1(
      object,
      arguments1
    ),
    arguments2
  ),
  arguments3  
  
)

# or
function3(function2(function1(object, arguments1), arguments2), arguments3)
```


dplyr in action
========================================================
**Example 1**

```r
ispcrime %>%
  filter(substr(county, 1, 1) == "D", year %in% c(2014, 2015)) %>%
  mutate(totalCrime = violentCrime + propertyCrime) %>%
  select(year, county, totalCrime)
```

```
  year  county totalCrime
1 2014 De Kalb       2218
2 2014 De Witt        182
3 2014 Douglas        116
4 2014 Du Page      12576
5 2015 De Kalb       2173
6 2015 De Witt        140
7 2015 Douglas        173
8 2015 Du Page      12538
```


========================================================
**Example 2**

```r
ispcrime %>%
  left_join(regions) %>%
  group_by(region, county) %>%
  summarise(annualAvgCrime = sum(violentCrime, propertyCrime, na.rm = TRUE) / n()) %>%
  arrange(desc(annualAvgCrime))
```

```
# A tibble: 102 x 3
# Groups:   region [4]
   region   county    annualAvgCrime
   <fct>    <fct>              <dbl>
 1 Cook     Cook              182818
 2 Northern Du Page            14316
 3 Northern Lake               12779
 4 Northern Winnebago          12275
 5 Northern Will               11078
 6 Southern St. Clair           9262
 7 Central  Sangamon            8876
 8 Northern Kane                8332
 9 Central  Peoria              7229
10 Central  Champaign           6567
# ... with 92 more rows
```


More on dplyr
========================================================
* `dplyr` on [tidyverse.org](http://dplyr.tidyverse.org/)
* `dplyr` [CRAN documentation](https://cran.r-project.org/web/packages/dplyr/dplyr.pdf)
* `dplyr` [Github repository](https://github.com/tidyverse/dplyr)


Tidying Up Your Data
========================================================
type:section
<img src="../images/tidyr.png" title="plot of chunk unnamed-chunk-31" alt="plot of chunk unnamed-chunk-31" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.tidyverse.org/">tidyverse.org</a>
</div>


Remember "tidy data"?
========================================================
<img src="../images/tidy-1.png" title="plot of chunk unnamed-chunk-32" alt="plot of chunk unnamed-chunk-32" width="100%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="http://r4ds.had.co.nz/">R for Data Science</a>
</div>


Key tidyr functions
========================================================
* `gather()`
* `spread()`
* `unite()`
* `separate()`
* `separate_rows()`


Make "wide" data longer
========================================================

```r
gather(tbl, key = "key", value = "value", ..., na.rm = FALSE, ...)
```
* The first argument is a tabular data object
    * e.g. `data.frame` or `tibble`
* `key` is a column to be used as a key, and `value` is a selection of columns to be used as values to each key value.


Make "long" data wider
========================================================

```r
spread(tbl, key, value, fill = NA, ...)
```
* The first argument is a tabular data object
* `gather()` and `spread()` complements


========================================================
**Example**



========================================================



Unite multiple columns into one
========================================================

```r
unite(tbl, col, ..., sep = "_", remove = TRUE)
```
* The first argument is a tabular data object
* `separate()` and `unite()` are complements


Split a column into many
========================================================

```r
separate(tbl, col, into, sep = "[^[:alnum:]]+", remove = TRUE, ...)
```
* The first argument is a tabular data object


========================================================
**Example**


========================================================



Split a row into many
========================================================

```r
separate_rows(tbl, ..., sep = "[^[:alnum:]]+", ...)
```
* The first argument is a tabular data object
* `separate_rows()` is similar to `separate()`, except the former results in a longer table while the latter results in a wider table. 

========================================================
**Example**



More on tidyr
========================================================
* `tidyr` on [tidyverse.org](http://tidyr.tidyverse.org/)
* `tidyr` [CRAN documentation](https://cran.r-project.org/web/packages/tidyr/tidyr.pdf)
* `tidyr` [Github repository](https://github.com/tidyverse/tidyr)


Questions?
========================================================
type: section
<img src="https://media.giphy.com/media/106cqwD4WrDjJm/giphy.gif" title="plot of chunk unnamed-chunk-43" alt="plot of chunk unnamed-chunk-43" width="50%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://media.giphy.com/media/106cqwD4WrDjJm/giphy.gif">giphy.com</a>
</p>


========================================================
References
<ul style="font-size: 0.6em">
  <li>Grolemund, G. & Wickham, H. (2017). <a href="http://r4ds.had.co.nz/"><span style="font-style:italic">R for Data Science</span></a>.</li>
  <li>RStudio. (2017). <a href="https://www.rstudio.com/resources/cheatsheets/">"Data Import Cheat Sheet"</a>.</li>
  <li>RStudio. (2017). <a href="https://www.rstudio.com/resources/cheatsheets/">"Data Transformation Cheat Sheet"</a>.</li>
  <li>Tidyverse. (n.d.). <a href="http://dplyr.tidyverse.org/"><span style="font-style:italic">dplyr.tidyverse.org</span></a>.</li>
  <li>Tidyverse. (n.d.). <a href="http://tidyr.tidyverse.org/"><span style="font-style:italic">tidyr.tidyverse.org</span></a>.</li>
  <li>Tidyverse. (n.d.). <a href="http://www.tidyverse.org/"><span style="font-style:italic">tidyverse.org</span></a>.</li>
</ul>


========================================================
type: section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Ic_pause_circle_outline_48px.svg/2000px-Ic_pause_circle_outline_48px.svg.png" title="plot of chunk unnamed-chunk-44" alt="plot of chunk unnamed-chunk-44" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>


