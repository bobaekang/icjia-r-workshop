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
<a href="../notes/module3_notes2.html">
  <button type="button">Notes</button>
</a>
</div>


# presentation
R Workshop
========================================================
type: slide-body
css: ../css/style_slides.css
<h3 style="color: #789">Module 3: Data analysis with R (2)</h3>  
2018-03-28  
Bobae Kang  
<small>(Bobae.Kang@illinois.gov)</small>


Agenda
========================================================
<div style="text-align:center; margin-top:10%;">
<ul style="list-style: none">
<li>
  Part 1: Getting started with tidyverse</li>
<li style="color: #00061a; font-size: 1.1em; font-weight:700">
  Part 2: More on data analysis</li>
</div>


More on Data Analysis
========================================================
type:section
<img src="../images/more_data_analysis.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" width="35%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cdn4.iconfinder.com/data/icons/basic-dashboard-1/512/Basic_Dashboard_UI_fix_option_machine_tools-512.png">Iconfinder.com</a>
</div>


More on Data Analysis
========================================================
type:section
<div style="text-align: center;">
<ol>
<li>Working with strings</li>
<li>Working with date/datetimes</li>
<li>Importing/exporting data</li>
<ol>
</div>

Working with Strings
========================================================
type:section
<img src="../images/font_case.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" width="33%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cdn3.iconfinder.com/data/icons/metro-design/512/font_case-512.png">Iconfinder.com</a>
</div>


stringr from tidyverse
========================================================
type:section
<img src="../images/stringr.png" title="plot of chunk unnamed-chunk-3" alt="plot of chunk unnamed-chunk-3" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.rstudio.com/">RStudio</a>
</div>


Key stringr functions
========================================================
* `function1()`
* `function2()`
* `function3()`
* `function4()`


function1
========================================================

```r
function()
```
* as the first argument


========================================================
**Example**



========================================================
**Base R alternative**



function2
========================================================

```r
function()
```
* as the first argument


========================================================
**Example**




========================================================
**Base R alternative**



function3
========================================================

```r
function()
```
* as the first argument


========================================================
**Example**




========================================================
**Base R alternative**



function4
========================================================

```r
function()
```
* as the first argument


========================================================
**Example**




========================================================
**Base R alternative**



More on stringr
========================================================
* `stringr` on [tidyverse.org](http://stringr.tidyverse.org/)
* `stringr` [CRAN documentation](https://cran.r-project.org/web/packages/stringr/stringr.pdf)
* `stringr` [Github repository](https://github.com/tidyverse/stringr)


Regular expression (regex)
========================================================
* What it is
* When to use/why useful


Regular expression in R
========================================================
* Finding regex matches
* Replacing regex matches


Finding regex matches
========================================================
* `grep()`
* `grepl()`
* `regexpr()`
* `gregexpr()`
* `regmatches()`


grep()
========================================================

```r
grep()
```
* as the first argument


========================================================
**Example**



grepl()
========================================================

```r
grepl()
```
* as the first argument


========================================================
**Example**



regexpr()
========================================================

```r
regexpr()
```
* as the first argument


========================================================
**Example**



gregexpr()
========================================================

```r
gregexpr()
```
* as the first argument


========================================================
**Example**



regmatches()
========================================================

```r
regmatches()
```
* as the first argument


========================================================
**Example**



Replacing regex matches
========================================================
* `sub()`
* `gsub()`


sub()
========================================================

```r
sub()
```
* as the first argument


========================================================
**Example**



gsub()
========================================================

```r
gsub()
```
* as the first argument


========================================================
**Example**



More on regular expression
========================================================
* resources


Working with Dates/Datetimes
========================================================
type:section
<img src="../images/calendar.png" title="plot of chunk unnamed-chunk-30" alt="plot of chunk unnamed-chunk-30" width="33%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://cdn4.iconfinder.com/data/icons/small-n-flat/24/calendar-512.png">Iconfinder.com</a>
</div>


Dates/Datetimes basics
========================================================
* basics


lubridate from tidyverse
========================================================
type:section
<img src="../images/lubridate.png" title="plot of chunk unnamed-chunk-31" alt="plot of chunk unnamed-chunk-31" width="25%" style="box-shadow: none; display: block; margin: auto;" />
<div style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://www.rstudio.com/">RStudio</a>
</div>


Key lubridate functions
========================================================
* `function1()`
* `year()`, `month()`, `day()`, `hour()`, ...
* `function2()`
* `function3()`


function1
========================================================

```r
function()
```
* as the first argument


========================================================
**Example**



========================================================
**Base R alternative**



function2
========================================================

```r
function()
```
* as the first argument


========================================================
**Example**




========================================================
**Base R alternative**



function3
========================================================

```r
function()
```
* as the first argument


========================================================
**Example**




========================================================
**Base R alternative**



function4
========================================================

```r
function()
```
* as the first argument


========================================================
**Example**




========================================================
**Base R alternative**



More on lubridate
========================================================
* `lubridate` on [tidyverse.org](http://lubridate.tidyverse.org/)
* `lubridate` [CRAN documentation](https://cran.r-project.org/web/packages/lubridate/lubridate.pdf)
* `lubridate` [Github repository](https://github.com/tidyverse/lubridate)


Importing/Exporting Data
========================================================
type:section
<img src="../images/data_transfer.png" title="plot of chunk unnamed-chunk-44" alt="plot of chunk unnamed-chunk-44" width="33%" style="box-shadow: none; display: block; margin: auto;" />
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


read_csv() and write_csv()
========================================================

```r
read_csv()
write_csv()
```
* `read_csv()`: output is a `tibble` object
* `write_csv()`: output is a .csv file


fread() and fwite()
========================================================

```r
fread()
fwrite()
```
* `fread` : output is a `data.table` object
* `fwrite`: output is a .csv file


========================================================
**Base R alternative**

Excel spreadsheets (.xlsx/.xls)
========================================================
* `readxl` package (tidyverse)
    * `read_excel()`
    * `write_excel()`


read_excel() write_excel()
========================================================

```r
read_excel()
write_excel()
```
* `read_excel()`: output is a `tibble` object
* `write_excel()`: output is an excel file


More on readxl
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


read_sav() write_sav()
========================================================

```r
read_sav()
write_sav()
```
* `read_sav()`: output is a `tibble` object
* `write_sav()`: output is an SPSS data file


More on haven
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


read_sav() write_sav()
========================================================

```r
read_feather()
write_feather()
```
* `read_feather()`: output is a `tibble` object
* `write_feather()`: output is a feather file


More on feather
========================================================
* `feather` on [tidyverse.org](http://haven.tidyverse.org/)
* `feather` [CRAN documentation](https://cran.r-project.org/web/packages/haven/haven.pdf)


Questions?
========================================================
type: section
<img src="https://cdn.dribbble.com/users/433975/screenshots/1627606/question-mark-dribbble.gif" title="plot of chunk unnamed-chunk-50" alt="plot of chunk unnamed-chunk-50" width="40%" style="display: block; margin: auto; box-shadow: none;" />
<p style="font-size:0.5em; text-align:center; color: #777;">
Source: <a href="https://dribbble.com/shots/1627606-question-mark">Joel Ploz</a>
</p>


References
========================================================
<ul style="font-size: 0.6em; list-style-type:none">
  <li><a href="#">1</a></li>
  <li><a href="#">2</a></li>
  <li><a href="#">3</a></li>
  <li><a href="#"></a></li>
</ul>
