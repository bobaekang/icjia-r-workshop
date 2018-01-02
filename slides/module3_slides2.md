# template elements
<div class="header"></div>
<div class="footer"></div>
<img src="http://www.icjia.state.il.us/_themes/icjia/img/logo-icjia-small-blue-3.png" class="logo"></img>
<img src="https://www2.illinois.gov/PublishingImages/seal.gif" class="seal"></img>


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 3: Data analysis with R (2)</h3>  
2018-01-01  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
  <p>Session 1: Getting started with tidyverse</p>
  <p style="color: #00061a; font-size: 1.1em; font-weight:700">
    Session 2: More on data analysis</p>
</div>


More on Data Analysis
========================================================
type:section
<img src="https://d33wubrfki0l68.cloudfront.net/071952491ec4a6a532a3f70ecfa2507af4d341f9/c167c/images/hex-dplyr.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="20%" style="box-shadow: none; margin-left: 20%" /><img src="https://d33wubrfki0l68.cloudfront.net/5f8c22ec53a1ac61684f3e8d59c623d09227d6b9/b15de/images/hex-tidyr.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="20%" style="box-shadow: none; margin-left: 20%" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.tidyverse.org/">tidyverse.org</a>
</div>


Working with Strings
========================================================
type:section
<img src="https://www.rstudio.com/wp-content/uploads/2014/04/stringr.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.rstudio.com/">RStudio</a>
</div>


Key stringr functions
========================================================
* `arange()`


More on stringr
========================================================
* `stringr` on [tidyverse.org](http://stringr.tidyverse.org/)
* `stringr` [CRAN documentation](https://cran.r-project.org/web/packages/stringr/stringr.pdf)
* `stringr` [Github repository](https://github.com/tidyverse/stringr)


Working with Datetimes
========================================================
type:section
<img src="https://www.rstudio.com/wp-content/uploads/2014/04/lubridate.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.rstudio.com/">RStudio</a>
</div>


Key lubricate functions
========================================================
* `arange()`


More on lubridate
========================================================
* `lubridate` on [tidyverse.org](http://lubridate.tidyverse.org/)
* `lubridate` [CRAN documentation](https://cran.r-project.org/web/packages/lubridate/lubridate.pdf)
* `lubridate` [Github repository](https://github.com/tidyverse/lubridate)


Importing/Exporting Data
========================================================
type:section
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/40/Data-transfer.svg/2000px-Data-transfer.svg.png" title="plot of chunk unnamed-chunk-4" alt="plot of chunk unnamed-chunk-4" width="30%" style="box-shadow: none; display: block; margin: auto;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.wikimedia.org">Wikimedia.org</a>
</p>


Comma-separated values (.csv)
========================================================
* `readr` package (tidyverse)
    * `read_csv()`
    * `write_csv()`
* `data.table` package
    * `fread()`
    * `fwrite()`


Excel spreadsheets (.xlsx/.xls)
========================================================
* `readxl` package (tidyverse)
    * `read_excel()`
    * `write_excel()`


========================================================
* `readxl` on [tidyverse.org](http://readxl.tidyverse.org/)
* `readxl` [CRAN documentation](https://cran.r-project.org/web/packages/readxl/readxl.pdf)
* `readxl` [Github repository](https://github.com/tidyverse/readxl)


SPSS data files (.sav)
========================================================
* `haven` package (tidyverse)
    * `read_sav()`
    * `write_sav()`
* `haven` also has functions to import/export the file formats of other statistical softwares
    * STATA
    * SAS


========================================================
* `haven` on [tidyverse.org](http://haven.tidyverse.org/)
* `haven` [CRAN documentation](https://cran.r-project.org/web/packages/haven/haven.pdf)
* `haven` [Github repository](https://github.com/tidyverse/haven)


A "fast-on-disk" data frame storage (.feather) 
========================================================
* `feather` package (tidyverse)
    * `read_feather()`
    * `write_feather()`
* The .feather format is also supported in Python!


========================================================
* `feather` on [tidyverse.org](http://haven.tidyverse.org/)
* `feather` [CRAN documentation](https://cran.r-project.org/web/packages/haven/haven.pdf)


Questions?
========================================================
type: section
<img src="https://cdn.dribbble.com/users/433975/screenshots/1627606/question-mark-dribbble.gif" title="plot of chunk unnamed-chunk-5" alt="plot of chunk unnamed-chunk-5" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://dribbble.com/shots/1627606-question-mark">Joel Ploz</a>
</p>
