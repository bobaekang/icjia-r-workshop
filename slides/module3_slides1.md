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
2018-01-01  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
  <p style="color: #00061a; font-size: 1.1em; font-weight:700">
    Session 1: Getting started with tidyverse</p>
  <p>Session 2: More on data analysis</p>
</div>


Getting Started with tidyverse
========================================================
type:section
<img src="https://d33wubrfki0l68.cloudfront.net/071952491ec4a6a532a3f70ecfa2507af4d341f9/c167c/images/hex-dplyr.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="20%" style="box-shadow: none; margin-left: 20%" /><img src="https://d33wubrfki0l68.cloudfront.net/5f8c22ec53a1ac61684f3e8d59c623d09227d6b9/b15de/images/hex-tidyr.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="20%" style="box-shadow: none; margin-left: 20%" />
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
<img src="https://d33wubrfki0l68.cloudfront.net/071952491ec4a6a532a3f70ecfa2507af4d341f9/c167c/images/hex-dplyr.png" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.tidyverse.org/">tidyverse.org</a>
</div>



Key dplyr functions
========================================================
* `arange()`
* `select()`
* `filter()`
* `mutate()`
* `group_by()` and `summarise()`
* `%>%`, the pipe operator


Sorting with arrange()
========================================================


Filtering with filter()
========================================================


Selecting with select()
========================================================


Transforming with mutate()
========================================================


Aggregating with group_by() and summarise()
========================================================


Chaining operations with %>%
========================================================


More on dplyr
========================================================
* `dplyr` on [tidyverse.org](http://dplyr.tidyverse.org/)
* `dplyr` [CRAN documentation](https://cran.r-project.org/web/packages/dplyr/dplyr.pdf)
* `dplyr` [Github repository](https://github.com/tidyverse/dplyr)


Tidying Up Your Data
========================================================
type:section
<img src="https://d33wubrfki0l68.cloudfront.net/5f8c22ec53a1ac61684f3e8d59c623d09227d6b9/b15de/images/hex-tidyr.png" title="plot of chunk unnamed-chunk-6" alt="plot of chunk unnamed-chunk-6" width="25%" style="box-shadow: none; display: block; margin: auto;" />
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


Fixing "long" data with spread()
========================================================


Splitting columns with separate()
========================================================


Combining columns with unite()
========================================================


Captuaring groups with extract()
========================================================


More on tidyr
========================================================
* `tidyr` on [tidyverse.org](http://tidyr.tidyverse.org/)
* `tidyr` [CRAN documentation](https://cran.r-project.org/web/packages/tidyr/tidyr.pdf)
* `tidyr` [Github repository](https://github.com/tidyverse/tidyr)


Questions?
========================================================
type: section
<img src="https://media.giphy.com/media/106cqwD4WrDjJm/giphy.gif" title="plot of chunk unnamed-chunk-7" alt="plot of chunk unnamed-chunk-7" width="50%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://media.giphy.com/media/106cqwD4WrDjJm/giphy.gif">giphy.com</a>
</p>


========================================================
type: section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Ic_pause_circle_outline_48px.svg/2000px-Ic_pause_circle_outline_48px.svg.png" title="plot of chunk unnamed-chunk-8" alt="plot of chunk unnamed-chunk-8" width="45%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>


